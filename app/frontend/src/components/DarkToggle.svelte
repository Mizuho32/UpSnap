<script>

    const preferesDark = window.matchMedia("(prefers-color-scheme: dark)");

    preferesDark.addEventListener("change", e => {
        setTheme(e.matches ? "dark" : "light");
    })

    if (localStorage.getItem("data-theme") === null) {
        setTheme(preferesDark.matches ? "dark" : "light");
    } else {
        setTheme(localStorage.getItem("data-theme"));
    }

	function setTheme(color) {
        if (color == "system") {
            document.documentElement.setAttribute("data-theme", preferesDark ? "dark" : "light");
            localStorage.setItem("data-theme", preferesDark ? "dark" : "light");
        } else {
            document.documentElement.setAttribute("data-theme", color);
            localStorage.setItem("data-theme", color);
        }
	}

</script>

<div class="dropdown">
    <button class="btn btn-light dropdown-toggle px-3 me-2 py-2" type="button" id="darkModeButton" data-bs-toggle="dropdown" aria-expanded="false">
        <i class="fa-solid fa-palette me-2"></i>Theme
    </button>
    <ul class="dropdown-menu" aria-labelledby="darkModeButton">
        <li>
            <button class="dropdown-item" on:click={() => setTheme("dark")}>
                <i class="fa-solid fa-moon me-2"></i>Dark
            </button>
        </li>
        <li>
            <button class="dropdown-item" on:click={() => setTheme("light")}>
                <i class="fa-solid fa-sun me-2"></i>Light
            </button>
        </li>
        <li>
            <button class="dropdown-item" on:click={() => setTheme("system")}>
                <i class="fa-solid fa-desktop me-2"></i>System
            </button>
        </li>
    </ul>
</div>
