<script>

    import AddForm from "./AddForm.svelte";

    export let isIssuePage;

</script>

<nav class="flex flex_space_between navbar">
    <div class="flex flex_row hdr_logos">
        <a class="flex flex_row flex_center flex_gap_10 logo" href="/">
            <img src="/icons/logo-icon.svg" alt="logo-icon" height="40px">
            <h2 class="hideForMob logo_tlt">TrackPro</h2>
        </a>

        {#if !isIssuePage}
            <div class="onlyForLap input search">
                <form action="?/search" method="post" class="flex">
                    <img src="/icons/search-icon.svg" alt="search" class="">
                    <input type="text" class="flex flex_row project_name" name="project_name" id="project_name" placeholder="Search by Project Name" >
                </form>
            </div>
        {/if}
    </div>

    <div class="flex flex_row flex_center flex_gap_10 hdr_fns">
        <div class="pointer add_prjt">
            {#if !isIssuePage}
                <button class="flex_gap_10 uppercase" onclick="onClickAddProject()">
                    <span>Add Project</span>
                    <span><img src="/icons/add-icon.svg" alt="add-icon"></span>
                </button>
            {/if}

            <div class="hidden add_form" id="add_form">
                <AddForm action="?/addProject" projectName="Project" />
            </div>

            <script>
                function onClickAddProject() {
                    document.getElementById("background").classList.remove("hidden");
                    document.getElementById("add_project_form").classList.remove("hidden");
                    document.getElementById("add_form").classList.remove("hidden");
                }
            </script>
        </div>
        
        
        <div class="onlyForMob hamburger">
            <div class="hamburger-icon" onclick="onclickhamburger()">
                <img src="/icons/hamburger-icon.svg" alt="hamburger-icon">
            </div>

            <div class="flex flex_col flex_gap_10 hidden mobile_nav" id="mobile_nav">
                <div class="input search">
                    <form action="" method="post" class="flex">
                        <img src="/icons/search-icon.svg" alt="search" class="">
                        <input type="text" class="flex flex_row" placeholder="Search Project" autofocus>
                    </form>
                </div>

                <div class="flex flex_row w-100 flex_center flex_space_between user_details_mob">
                    <div class="input user">
                        <span>
                            <img src="/icons/user-icon.svg" alt="user" class="user_img">
                        </span>
                        <input type="text" value="User" disabled>
                        <span>
                            <img src="/icons/down-arrow-color-icon.svg" alt="down-arrow" class="drop_down_arrow">
                        </span>
                    </div>

                    <div class="pointer mob_bg mob_bg_noti">
                        <img src="/icons/noti-icon.svg" alt="noti">
                    </div>

                    <div class="pointer mob_bg mob_bg_setting">
                        <img src="/icons/setting-icon.svg" alt="settings-icon">
                    </div>
                </div>

                <div class="flex flex_center flex_space_between input logout">
                    <input type="text" value="Logout" disabled> 
                    <span>
                        <img src="/icons/sign-out-icon.svg" alt="signout" style="margin-top: 5px;">
                    </span>
                </div>
            </div>
            

            <script>
                function onclickhamburger() {
                    const menuIcon = document.getElementById("mobile_nav");

                    menuIcon.classList.toggle("hidden");
                }
            </script>
        </div>

        <div class="pointer hideForMob notifications">
            <img src="/icons/noti-icon.svg" alt="noti">
        </div>
        <div class="pointer hideForMob ur_dtls">
            <div class="input user">
                <span>
                    <img src="/icons/user-icon.svg" alt="user" class="user_img">
                </span>
                <input type="text" value="User" disabled>
                <span>
                    <img src="/icons/down-arrow-color-icon.svg" alt="down-arrow" class="drop_down_arrow">
                </span>
            </div>
        </div>
        <div class="pointer hideForMob settings">
            <img src="/icons/setting-icon.svg" alt="settings-icon">
        </div>
    </div>
</nav>

<style>
    .navbar {
        padding: 17px 20px;
        border-bottom: 1px solid #F1ECFF;
        align-items: center;
        position: fixed;
        width: 100%;
        background-color: #fff;
        z-index: 5;
    }

    .logo {
        color: #111;
    }

    .input {
        background-color: #F1ECFF;
        padding: 0 25px;
        position: relative;
        border: 1px solid #F1ECFF;
        transition: all .3s ease-in-out;
    }

    .input:hover {
        border: 1px solid #b8a9e2;
    }

    .user {
        max-width: 150px;
        width: 100%;
    }

    .user_img {
        position: absolute;
        left: 15px;
        top: 5px;
    }

    .drop_down_arrow {
        position: absolute;
        right: 15px;
        top: 8px;
    }

    .mobile_nav {
        position: absolute;
        left: 0;
        top: 60px;
        background-color: #C1B3E8;
        padding: 15px;
        width: 100%;
        transition: all 3s ease-out;
        z-index: 5;
    }

    .mob_bg {
        background-color: #F1ECFF;
    }

    .mob_bg_noti {
        padding: 9px 25px;
    }

    .mob_bg_setting {
        padding: 3px 25px;
    }

    @media(min-width: 768px) {
        .hdr_fns {
            gap: 30px;
        }

        .input {
            border-radius: 35px;
        }

        .search {
            max-width: 380px;
            width: 100%;
        }
    }

    @media(min-width: 1200px) {
        .navbar {
            max-height: 80px;
        }

        .hdr_logos {
            gap: 75px;
        }

        .hdr_fns {
            gap: 30px;
        }
    }

</style>