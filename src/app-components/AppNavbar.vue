<template>
    <div class="app-navbar">
        <b-navbar toggleable="lg" type="light">
            <b-navbar-brand href="#">BrandName</b-navbar-brand>

            <b-navbar-toggle target="nav-collapse"></b-navbar-toggle>

            <b-collapse id="nav-collapse" is-nav>
            <b-navbar-nav>
                <b-nav-item-dropdown text="Compagnies" class="text-warning"></b-nav-item-dropdown>
                <b-nav-item-dropdown text="Inventory"></b-nav-item-dropdown>
                <b-nav-item-dropdown text="Contacts" ></b-nav-item-dropdown>
                <b-nav-item-dropdown text="Settings" ></b-nav-item-dropdown>
            </b-navbar-nav>

            <!-- Right aligned nav items -->
            <b-navbar-nav class="ml-auto">

                <b-nav-item-dropdown text="Mykulas Baskyd" right class="mr-3">
                <b-dropdown-item> <i class="fas fa-user"></i> Profile</b-dropdown-item>
                <b-dropdown-item><i class="fas fa-cog"></i> Settings</b-dropdown-item>
                <b-dropdown-item><i class="fas fa-sign-out-alt"></i> Sign out</b-dropdown-item>
                </b-nav-item-dropdown>

            </b-navbar-nav>
            </b-collapse>
        </b-navbar>            
    </div>
</template>

<script>
export default {
    name: 'AppNavbar',
    data: () => ({
        
    })
}
</script>