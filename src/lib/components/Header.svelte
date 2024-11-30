<script>
    let navElement;
    let hamburgerElement;
    let state = $state(0);

    const isActive = () => {
      if (state === 0) {
        navElement.classList.add("isActive");
        hamburgerElement.classList.add("isActive");
        state = 1;
      } else {
        navElement.classList.remove("isActive");
        hamburgerElement.classList.remove("isActive");
        state = 0;
      }
    };

    const handleResize = () => {
      if (window.innerWidth > 744) {
        navElement?.classList.remove("isActive");
        hamburgerElement?.classList.remove("isActive");
        state = 0;
      }
    };

    
    $effect(() => {
      if (hamburgerElement) {
        hamburgerElement.addEventListener('click', isActive);

        return () => {
          hamburgerElement?.removeEventListener('click', isActive);
        };
      }
    });

</script>

<header>
    <div class="wrapper">
        <div class="wrapper-logo">
            <img src="https://upload.wikimedia.org/wikipedia/commons/6/6c/Westb%C3%B6hmische_Universit%C3%A4t_Pilsen_Logo.svg" alt="">
        </div>
        <nav bind:this={navElement} class:isActive={state == 1}>
            <a href="/">test</a>
            <a href="/">test</a>
            <a href="/">test</a>
        </nav>
        <div class="wrapper-hamburger" bind:this={hamburgerElement} class:isActive={state == 1}>
            <span></span>
            <span></span>
            <span></span>
        </div>
    </div>
</header>

<style lang="scss">

    header{
        height: 100px;
        margin: 0;
        padding: 0;
        box-shadow: rgba(0, 0, 0, 0.24) 0px 3px 8px;

        .wrapper{
            max-width: 1300px;
            margin: auto;
            display: flex;
            justify-content: space-between;
            height: 100px;
            align-items: center;


            .wrapper-logo{
                height: 100%;
                display: flex;
                justify-content: center;
                align-content: center;
                
                img{
                    width: 100%;
                }

            }

            nav{
                display: flex;
                justify-content: center;
                gap: 36px;
                margin-right: 36px;
                position: fixed;
                flex-direction: column;
                width: 100%;
                background-color: white;
                height: 100%;
                top: 0;
                left: 0;
                transform: translateX(100%);
                transition: ease .5s;

                &.isActive{
                    transform: translate(0);
                }


                @media (min-width: 768px){
                    position: relative;
                    display: flex;
                    justify-content: flex-end;
                    gap: 36px;
                    margin-right: 36px;
                    flex-direction: row;
                    background-color: none;
                    transform: translateX(0);
                }

                a{
                    text-decoration: none;
                    color: black;
                    font-weight: 500;
                    font-family: "Poppins", sans-serif;
                    font-weight: 500;
                    transition: ease .3s;
                    text-align: center;
                    display: flex;
                    justify-content: center;
                    align-items: center;

                    &:hover{
                        color: blue;
                    }
                }
            }

            .wrapper-hamburger{
                position: absolute;
                right: 36px;
                top: 0;
                height: 100px;
                display: flex;
                justify-content: center;
                align-items: center;
                gap: 10px;
                flex-direction: column;
                cursor: pointer;

                @media (min-width: 768px){
                    display: none;
                }

                span{
                    width: 50px;
                    border: 2px solid black;
                    border-radius: 10px;
                    transition: ease .3s;
                    opacity: 1;
                }

                &.isActive{
                    span:nth-child(1){
                        transform: translate(0, 7px)  rotate(45deg);
                    }
                    span:nth-child(2){
                        opacity: 0;
                    }
                    span:nth-child(3){
                        transform: translate(0px, -19px)  rotate(-45deg);
                    }
                }
            }
        }
    }

</style>