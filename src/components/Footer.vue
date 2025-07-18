<template>
  <footer class="footer">
    <div class="container">
      <div class="footer__logo">
        <img src="../assets/logo.png" alt="Logo" />
      </div>
      <nav class="footer__menu">
        <ul>
          <li><a href="#">Каталог</a></li>
          <li><a href="#">Доставка</a></li>
          <li><a href="#">Оплата</a></li>
          <li><a href="#">Контакты</a></li>
          <li><a href="#">О галерее</a></li>
        </ul>
      </nav>
      <div class="footer__contact">
        <div class="footer__contact-block">
          <div class="phone-icon"></div><div>+7 (495) 555-55-55</div> 
        </div>
        <div class="footer__contact-block">
          <div class="location-icon"></div><div>г. Москва, ул. Расплетина, 24</div>
        </div>
      </div>
    </div>
  </footer>
</template>

<style scoped>
.footer {
  background-color: var(--bg-main);
  border-top: 1px solid #E1E1E1;
  padding: 24px 10px;
  margin-top: 45px;
}
.container {
  max-width: 1200px;
  margin: 0 auto;
  display: flex;
  justify-content: space-between;
  align-items: center;
}
.footer__logo img {
  width: 50px;
}
.footer__menu ul {
  padding: 0;
  list-style: none;
  display: flex;
  gap: 48px;
}
.footer__menu li a {
  font-size: var(--font-main);
  text-decoration: none;
  color: var(--color-main);
}
.footer__contact {
  display: flex;
  align-items: center;
}
.footer__contact-block {
  display: flex;
  align-items: center;
  margin-right: 48px;
}
.phone-icon,
.location-icon {
  width: 21px;
  height: 21px;
  margin-right: 10px;
  background-image: url('../assets/phone.png');
  background-position: center;
  background-repeat: no-repeat;
  background-size: contain;
}
.location-icon {
  background-image: url('../assets/location.png');
  width: 15px;
}
.footer__contact  div {
  font-size: var(--font-small);
}

@media (max-width: 1024px) {
  .footer__menu ul {
    gap: 16px;
  }
  .footer__menu li a {
    font-size: 14px;
  }
  .footer__contact  {
    flex-wrap: wrap;
    justify-content: space-around;
  }
  .footer__contact  div {
    font-size: 14px;
  }
  .footer__contact-block {
   margin-right: 10px;
}
  .phone-icon,
  .location-icon {
    width: 14px;
    height: 14px;
    margin-right: 5px;
  }
  .location-icon {
    width: 10px;
  }
}

@media (max-width: 705px) {
  .container {
    flex-direction: column;
  }
   .footer__menu {
    display: none;
  }
  .footer__contact {
    flex-direction: column;
    align-items: center;
    justify-content: flex-start;
  }
  .footer__contact-block {
    margin: 20px 0 5px 0;
  }
}
</style>