<template>
    <div class="app-header">
        <header>
            <h2>Brightness & Contrast Developer Test</h2>
            <h3>01 Jun, 2018 - 31 Dec, 2019</h3>
        </header>
        <div class="hero-image">
            <img src="@/assets/images/pleasure-garden.jpg" alt="Pleasure Garden"/>
            <div class="hero-wrapper">
                <div class="hero"></div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: 'AppHeader'
}
</script>

<style lang="scss" scoped>
    $purple: #7144C3;
    $green: #23A15E;
    $blue: #5D83BF;

    .app-header{
        header{
            background: $purple;
            color: #fff;
            text-align: center;
            padding: 25px 0;
            h3{
                font-weight:normal;
            }
        }
        .hero-image{
            position:relative;
            margin-bottom: 30px;
            >img{
                display:block;
                width:100%;
            }
            .hero-wrapper{
                position: absolute;
                left:0;
                right:0;
                width: 100%;
                background: transparent;
                z-index: 5;
                bottom:-25px;
                .hero{
                    background: url(https://media.licdn.com/dms/image/C5603AQEctBdE-mLgrw/profile-displayphoto-shrink_200_200/0?e=1554336000&v=beta&t=KkPxqNbNTGt4mMXno4ca0gOQmL1BRDHuhkaKsix3p0s) no-repeat center center;
                    width: 150px;
                    height: 150px;
                    margin: 0 auto;
                    border-radius: 50%;
                    border: 4px solid #fff;
                }
            }
        }
    }
</style>
