<template>
    <div id="navbar">
        <div id="wrapper">

            <aside id="sidebar-wrapper">
              <div class="sidebar-brand" style="background: #222;">
                  <h2><span style="color:#fff">T</span><span style="color:orange">M</span></h2>
              </div>
              <ul class="sidebar-nav">
                  <li class="active">
                  <a href="#" title="Accueil"><i class="fa fa-home"></i>Qui sommes-nous ?</a>
                  </li>
                  <li>
                  <a href="#" title="Modules"><i class="fa fa-plug"></i>Notre Solution</a>
                  </li>
                  <li>
                  <a href="#" title="Demo"><i class="fa fa-window-maximize"></i>Démo</a>
                  </li>
              </ul>
              <div class="position-absolute top-50 translate-middle" style="right: 0; position: block;
    width: -moz-max-content;
    width: max-content;
    margin: 0 10px;
    text-align: center;
    padding: 0 20px;">
                <ul class="sidebar-nav justify-content-end">
                  <li>
                    <a href="#" title="Contact"><i class="fa fa-phone"></i>Contact</a>
                  </li>
                </ul>
              </div>
            </aside>
          </div>
    </div>
</template>

<script>

</script>

<style>

/* scrollbar */
/* width */
::-webkit-scrollbar {
  width: 0px;
	background-color: #F5F5F5;
}

/* Track */
::-webkit-scrollbar-track {
  -webkit-box-shadow: inset 0 0 6px rgba(0,0,0,0.3);
	border-radius: 10px;
	background-color: #F5F5F5;
}

/* Handle */
::-webkit-scrollbar-thumb {
  border-radius: 10px;
	-webkit-box-shadow: inset 0 0 6px rgba(0,0,0,.3);
	background-color: #555;
}

/* Handle on hover */
::-webkit-scrollbar-thumb:hover {
  background: #555;
}

a {
  transition: background 0.2s, color 0.2s;
}
a:hover,
a:focus {
  text-decoration: none;
}

#wrapper {
  padding-left: 0;
  transition: all 0.5s ease;
  position: relative;
}

#sidebar-wrapper {
  display: flex;
  z-index: 1000;
  position: fixed;
  left: 250px;
  width: 0;
  height: 65px;
  margin-left: -250px;
  overflow-y: auto;
  overflow-x: hidden;
  background: #fff;
  transition: all 0.5s ease;
}

#wrapper.toggled #sidebar-wrapper {
  width: 65px;
}

.sidebar-brand {
  position: block;
  width: max-content;
  text-align: center;
  padding: 20px 30px;
}
.sidebar-brand h2 {
  margin: 0;
  font-weight: 600;
  font-size: 24px;
  color: #222;
}

.sidebar-nav {
  display: flex;
  position: block;
  width: 65px;
  margin: 0;
  padding: 0;
  list-style: none;
}
.sidebar-nav > li {
  line-height: 42px;
}
.sidebar-nav > li a {
  display: flex;
  align-items: center;
  width: max-content;
  height: 65px;
  padding: 2px 5px 2px 0;
  text-decoration: none;
  color: #222;
  font-weight: 600;
  font-size: 18px;
}
.sidebar-nav > li > a:hover,
.sidebar-nav > li.active > a {
  text-decoration: none;
  color: #fff;
  background: orange;
}
.sidebar-nav > li > a i.fa {
  font-size: 20px;
  width: 50px;
}

#navbar-wrapper {
    width: 100%;
    position: absolute;
    z-index: 2;
}
#wrapper.toggled #navbar-wrapper {
    position: absolute;
    margin-right: -250px;
}
#navbar-wrapper .navbar {
  border-width: 0 0 0 0;
  background-color: #eee;
  font-size: 24px;
  margin-bottom: 0;
  border-radius: 0;
}
#navbar-wrapper .navbar a {
  color: #757575;
}
#navbar-wrapper .navbar a:hover {
  color: #F8BE12;
}

#content-wrapper {
  width: 100%;
  position: absolute;
  padding: 15px;
  top: 100px;
}
#wrapper.toggled #content-wrapper {
  position: absolute;
  margin-right: -250px;
}

@media (min-width: 992px) {
  #wrapper {
    padding-left: 250px;
  }
  
  #wrapper.toggled {
    padding-left: 60px;
  }

  #sidebar-wrapper {
    width: 100vw;
  }
  
  #wrapper.toggled #sidebar-wrapper {
    width: 60px;
  }
  
  #wrapper.toggled #navbar-wrapper {
    position: absolute;
    margin-right: -190px;
}
  
  #wrapper.toggled #content-wrapper {
    position: absolute;
    margin-right: -190px;
  }

  #navbar-wrapper {
    position: relative;
  }

  #wrapper.toggled {
    padding-left: 60px;
  }

  #content-wrapper {
    position: relative;
    top: 0;
  }

  #wrapper.toggled #navbar-wrapper,
  #wrapper.toggled #content-wrapper {
    position: relative;
    margin-right: 60px;
  }
}

@media (min-width: 768px) and (max-width: 991px) {
  #wrapper {
    padding-left: 60px;
  }

  #sidebar-wrapper {
    width: 60px;
  }
  
#wrapper.toggled #navbar-wrapper {
    position: absolute;
    margin-right: -250px;
}
  
  #wrapper.toggled #content-wrapper {
    position: absolute;
    margin-right: -250px;
  }

  #navbar-wrapper {
    position: relative;
  }

  #wrapper.toggled {
    padding-left: 250px;
  }

  #content-wrapper {
    position: relative;
    top: 0;
  }

  #wrapper.toggled #navbar-wrapper,
  #wrapper.toggled #content-wrapper {
    position: relative;
    margin-right: 250px;
  }
}

@media (max-width: 767px) {
  #wrapper {
    padding-left: 0;
  }

  #sidebar-wrapper {
    width: 0;
  }

  #wrapper.toggled #sidebar-wrapper {
    width: 65px;
  }
  #wrapper.toggled #navbar-wrapper {
    position: absolute;
    margin-right: -250px;
  }

  #wrapper.toggled #content-wrapper {
    position: absolute;
    margin-right: -250px;
  }

  #navbar-wrapper {
    position: relative;
  }

  #wrapper.toggled {
    padding-left: 250px;
  }

  #content-wrapper {
    position: relative;
    top: 0;
  }

  #wrapper.toggled #navbar-wrapper,
  #wrapper.toggled #content-wrapper {
    position: relative;
    margin-right: 250px;
  }
}
</style>