<html lang="pt-br">
  <head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1, maximum-scale=1.0">
    <title></title>
    <!--CSS integrado--> 
    <style>
      /*formatação da página*/
      * {
        margin: 0;
        padding: 0;
        
      }
      body {
      
          font: 300 18px/1.6 "Source Sans Pro",sans-serif;
          text-align: center;
          background: #100a1c;
           radial-gradient(50% 30% ellipse at center top, #201e40 0%, rgba(0,0,0,0) 100%),
           radial-gradient(60% 50% ellipse at center bottom, #261226 0%, #100a1c 100%);
	      
      }
      /*links*/
      a {
        color: #fff;
        text-decoration: none;
        transition: 0.3s;
      }
      /*efeito ao clicar nos links*/
      a:hover {
        opacity: 0.7;
      }
      /*estilo da logo*/
      .logo {
        font-size: 24px;
        text-transform: uppercase;
        letter-spacing: 4px;
      }
      /*nav*/
      nav {
        display: flex; /*um do lado do outro*/
        justify-content: space-around;
        align-items: center;
        font: 300 20px/1.6 "Source Sans Pro",sans-serif;
        background: #23232e;
        height: 8vh; /*unidade responsiva que se adapta a altura da janela de visualização do usuário*/
      }

      p { /*parafrafos em geral*/
          text-align: justify;
          margin-left:  20px;
          margin-right:  20px;
          padding: 0 ;
          color:#fff;
          font: 300 15px/1.6 "Source Sans Pro",sans-serif;
       }
      
      
      main {
        background: url("fundo.jpeg") no-repeat 
        center center;
        background-size: cover ;
        height: 100vh;
      }
      /*ul*/
      
      .nav-list {
        list-style: none;
        display: flex;
      }
      
      .nav-list li {
        letter-spacing: 3px;
        margin-left: 32px;
      }
      .mobile-menu {
        display: none;
        cursor: pointer;
      }
      .mobile-menu div {
       
        width: 32px;
        height: 2px;
        background: #fff;
        margin: 8px;
        transition: 0.3s;
      }
      /*media query para dispositivos*/
      @media (max-width: 999px) {
    
        body {
          overflow-x: hidden;
          
        }
       
        .nav-list {
          position:absolute;
          top: 8vh;
          right: 0;
          width: 100vw;
          height: 92vh;
          background: #23232e;
          flex-direction: column;
          align-items: center;
          justify-content: space-around;
          transform: translateX(100%);
          transition: transform 0.3s ease-in;
        }
        .nav-list li {
          margin-left: 0;
          opacity: 0;
        }
        .mobile-menu {
          display: block;
          
        }  
             /*active classe adicionada através do JavaScript*/
        .nav-list.active {
          overflow-x: hidden;
          transform: translateX(0);
        }
        @keyframes navLinkFade {
          from {
            opacity: 0;
            transform: translateX(50px);
          }
          to {
            opacity: 1;
            transform: translateX(0px);
            
          }
        }
        .mobile-menu.active .line1 {
           transform: rotate(-45deg) translate(-8px, 8px);
        }
        
        .mobile-menu.active .line2 {
            opacity: 0;
        }
        
        .mobile-menu.active .line3 {
          transform: rotate(45deg) translate(-5px, -7px);
        }
        
      }
    </style>
  </head>
  
  <body>
    <!--Usando tags semanticas-->
    <header>
      <nav>
        <a class="logo" href="#">Vitor Oliveira</a>
        
      
        <!--menu móvel-->
        <div class="mobile-menu">
          <div class="line1"></div>
          <div class="line2"></div>
          <div class="line3"></div>
        </div>
       
        <!--items do menu-->
        <ul class="nav-list">
          <li><a href="https://github.com/VitorDev01">Git Hub</a></li>
          <li><a href="mailto:victorskw89@gmail.com">Gmail</a></li>
          <li><a href="https://www.instagram.com/vitor_.77/">Instagram</a></li>
          <li><a href="https://www.facebook.com/profile.php?id=100078322466753">Facebook</a></li>
        </ul>
   
      </nav>
    </header>
    <!--tag main para por o fundo-->
    
        
         <p>Programador Front End, conhecimentos autodidata em HTML5 CSS3 e JavaScript, pretendo cursar Análise e Desenvolvimento De Sistemas, fã do raciocínio lógico  amo café e estou sempre buscando aperfeiçoar meu inglês.</p>
         <p>Tendo começado essa jornada na programação em 2019 com os professores Gustavo Guanabara e Bruno Campos dos canais Curso em video e CFB cursos.</p>
        
    
    







    
    <!--JavaScript Integrado-->
    <script>
 
        class MobileNavbar {
          constructor(mobileMenu, navList, navLinks) {
            this.mobileMenu = document.querySelector(mobileMenu);
            this.navList = document.querySelector(navList);
            this.navLinks = document.querySelectorAll(navLinks);
            this.activeClass = "active";
        
            this.handleClick = this.handleClick.bind(this);
          }

          animateLinks() {
            this.navLinks.forEach((link, index) => {
              link.style.animation
                ? (link.style.animation = "")
                : (link.style.animation = `navLinkFade 0.5s ease forwards ${
                    index / 7 + 0.3
                  }s`);
            });
          }

          handleClick() {
            this.navList.classList.toggle(this.activeClass);
            this.mobileMenu.classList.toggle(this.activeClass);
            this.animateLinks();
          }

          addClickEvent() {
            this.mobileMenu.addEventListener("click", this.handleClick);
          }

          init() {
            if (this.mobileMenu) {
              this.addClickEvent();
            }
            return this;
          }
        }

        const mobileNavbar = new MobileNavbar(
          ".mobile-menu",
          ".nav-list",
          ".nav-list li",
        );
        mobileNavbar.init();
    </script>
  </body>
</html>
