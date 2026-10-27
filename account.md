---
layout: single
title: "Личный кабинет аквариумиста"
permalink: /account/
author_profile: true
header:
  overlay_image: /assets/images/Gos.jpg
  overlay_filter: 0.4
---

<!-- КОНТЕЙНЕР ДЛЯ ГОСТЕЙ (ЕСЛИ НЕ ВОШЕЛ) -->
<div id="guest-block" style="display: block;">
  <p style="font-size: 16px; line-height: 1.6;">Добро пожаловать в закрытый раздел Белорусского общества аквариумистов! Авторизуйтесь под своим личным паролем, чтобы получить доступ к профилю участника клуба.</p>
  
  <hr style="border: 0; height: 1px; background: #eee; margin: 20px 0;">
  
  <button id="login-trigger-btn" class="btn btn--info" style="font-weight: bold; border-radius: 4px; padding: 12px 24px; font-size: 16px;">
    <i class="fas fa-sign-in-alt"></i> Войти в аккаунт Белорусского общества аквариумистов
  </button>
</div>

<!-- КОНТЕЙНЕР ДЛЯ АВТОРИЗОВАННЫХ ПОЛЬЗОВАТЕЛЕЙ -->
<div id="user-block" style="display: none;">
  <div style="background-color: #f9f9f9; padding: 25px; border-radius: 8px; border: 1px solid #eee; margin: 20px 0; display: flex; align-items: center; gap: 20px;">
    <img id="user-card-avatar" src="" style="width: 80px; height: 80px; border-radius: 50%; border: 3px solid #00bcd4; box-shadow: 0 4px 10px rgba(0,0,0,0.1); object-fit: cover;">
    <div>
      <h3 style="margin: 0; color: #00bcd4; font-size: 22px;" id="user-card-name"></h3>
      <p style="margin: 5px 0 0 0; color: #666; font-size: 14px;"><i class="fas fa-id-card"></i> Статус: <b>Одобренный участник Белорусского общества аквариумистов</b></p>
      <p style="margin: 3px 0 0 0; color: #666; font-size: 14px;"><i class="fas fa-map-marker-alt"></i> Регион: <b>Беларусь</b></p>
    </div>
  </div>

  <hr style="border: 0; height: 1px; background: #eee; margin: 25px 0;">

  <h3>⚙️ Доступные функции клуба:</h3>
  <ul>
    <li>Просмотр закрытых материалов и архивов (разработан)</li>
    <li>Доступ к специальным файлам и памяткам для скачивания</li>
    <li>Прямая приоритетная связь с администрацией</li>
  </ul>
 

  <br>
  <button id="logout-trigger-btn" class="btn btn--danger" style="border-radius: 4px; padding: 8px 16px; font-size: 14px;">
    <i class="fas fa-sign-out-alt"></i> Выйти из кабинета
  </button>
</div>

<script>
  // Считываем базу данных из вашего файла _data/users.yml
  const accountsBase = [
    {% for user in site.data.users %}
      { username: "{{ user.username }}", password: "{{ user.password }}", name: "{{ user.name }}", avatar: "{{ user.avatar }}" }{% unless forloop.last %},{% endunless %}
    {% endfor %}
  ];

  function renderAccountPage() {
    const sessionData = localStorage.getItem("boa_user");
    const guestBlock = document.getElementById("guest-block");
    const userBlock = document.getElementById("user-block");

   
    if (sessionData) {
      // Если вошли — прячем блок гостя, показываем карту пользователя
      const currentUser = JSON.parse(sessionData);
      guestBlock.style.display = "none";
      userBlock.style.display = "block";
      
      document.getElementById("user-card-name").innerText = currentUser.name;
      document.getElementById("user-card-avatar").src = currentUser.avatar;
    } else {
      // Если не вошли — показываем форму входа
      guestBlock.style.display = "block";
      userBlock.style.display = "none";
    }
  }

  // Обработчик кнопки Войти
  document.getElementById("login-trigger-btn").addEventListener("click", function() {
    const loginInp = prompt("Введите ваш логин участника общества БОА:");
    if (!loginInp) return;
    const passInp = prompt("Введите ваш пароль доступа:");
    if (!passInp) return;

    const matched = accountsBase.find(u => u.username === loginInp.trim().toLowerCase() && u.password === passInp.trim());

    if (matched) {
      localStorage.setItem("boa_user", JSON.stringify(matched));
      alert(`С возвращением, ${matched.name}!`);
      window.location.reload();
    } else {
      alert("Ошибка: Неверный логин или секретный пароль. Доступ заблокирован.");
    }
  });

  // Обработчик кнопки Выйти
  document.getElementById("logout-trigger-btn").addEventListener("click", function() {
    if (confirm("Вы точно хотите выйти из аккаунта?")) {
      localStorage.removeItem("boa_user");
      window.location.reload();
    }
  });

  document.addEventListener("DOMContentLoaded", renderAccountPage);
</script>
