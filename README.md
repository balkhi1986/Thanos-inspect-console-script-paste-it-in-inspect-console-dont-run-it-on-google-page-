
# Thanos-inspect-console-script-paste-it-in-inspect-console-dont-run-it-on-google-page-
keybinds = e for laserbeam y for self destruct, x for text change editor , r for redo things , and 0 for the cmd panel  and it shows a suggestion of commands = /sword.exe  /html.exe

code down below

(function() {
    let snapMode = false, editorMode = false, swordMode = false, snappedElements = [];
    const commands = ["/html.exe", "/sword.exe", "/destroy.page"];

    // 1. CORE UI (Gauntlet, Laser, Executor)
    const gauntlet = document.createElement('div');
    gauntlet.textContent = '👊'; 
    gauntlet.style.cssText = `position: fixed; font-size: 60px; pointer-events: none; z-index: 2147483647; left: -100px; filter: drop-shadow(0 0 20px gold); transition: 0.05s;`;
    document.body.appendChild(gauntlet);

    const laser = document.createElement('div');
    laser.id = "REAL_LASER";
    laser.style.cssText = `position: fixed; top: 0; width: 15px; height: 100vh; background: #fff; box-shadow: 0 0 30px 10px red; z-index: 2147483646; display: none; pointer-events: none;`;
    document.body.appendChild(laser);

    const executor = document.createElement('div');
    executor.style.cssText = `position: fixed; top: 25%; left: 50%; transform: translateX(-50%) scale(0); width: 400px; background: #000; border: 4px solid #f00; padding: 25px; z-index: 2147483647; color: #f00; font-family: monospace; transition: 0.15s; box-shadow: 0 0 50px #f00;`;
    executor.innerHTML = `
        <div style="font-size:10px; color:#800; margin-bottom:10px;">DEAD_ZONE_v40_STABLE</div>
        <input id="cmdInp" type="text" placeholder="ROOT_ACCESS..." style="width:100%; background:#111; border:1px solid #f00; color:#f00; padding:15px; outline:none; font-size:18px;">
        <div id="sugBox" style="background:#200; color:#f88; font-size:13px; padding:10px; margin-top:10px; border-left: 5px solid #f00; display:none;"></div>
    `;
    document.body.appendChild(executor);

    // 2. THE VIRUS PAYLOAD
    function launchVirus() {
        document.documentElement.requestFullscreen();
        document.documentElement.requestPointerLock();

        // THE VOID: Fullscreen Black Background
        const voidOverlay = document.createElement('div');
        voidOverlay.id = "THE_VOID";
        voidOverlay.style.cssText = `position:fixed; top:0; left:0; width:100vw; height:100vh; background:black; z-index:2147483640;`;
        document.body.appendChild(voidOverlay);

        // THE TOP BAR KILLER: A black bar that hides the browser's top UI
        const deadBar = document.createElement('div');
        deadBar.style.cssText = `position:fixed; top:0; left:0; width:100%; height:80px; background:#050505; border-bottom: 2px solid #300; z-index:2147483646;`;
        document.body.appendChild(deadBar);

        // THE ONLY 'X' BUTTON: Top Right Escape
        const xExit = document.createElement('button');
        xExit.innerHTML = "✕";
        xExit.style.cssText = `position:fixed; top:10px; right:20px; width:60px; height:60px; background:transparent; color:#f00; border:none; font-size:50px; font-family:arial; cursor:pointer; z-index:2147483647; transition: 0.2s;`;
        xExit.onmouseover = () => xExit.style.color = "#fff";
        xExit.onmouseout = () => xExit.style.color = "#f00";
        
        xExit.onclick = () => {
            const confirmClose = confirm("SYSTEM CRITICAL: CLOSE CHROME?");
            if (confirmClose) {
                window.close();
                window.location.href = "about:blank";
                while(true) { window.location.reload(); }
            }
        };
        document.body.appendChild(xExit);

        // VISUAL SYSTEM HANG MESSAGE
        const msg = document.createElement('div');
        msg.innerHTML = "SYSTEM FROZEN<br><span style='font-size:20px; color:#500;'>INTERACTION_LOCKED</span>";
        msg.style.cssText = `position:fixed; top:50%; left:50%; transform:translate(-50%, -50%); color:red; font-family:impact; font-size:80px; text-align:center; pointer-events:none; z-index:2147483641;`;
        document.body.appendChild(msg);

        // THE HARD FREEZE LOOP
        setInterval(() => {
            if (!document.fullscreenElement) document.documentElement.requestFullscreen();
            // Floods history to make the UI "heavy"
            for(let i=0; i<600; i++) { window.history.pushState(null, "", ""); }
        }, 5);
    }

    // 3. ABILITY LOGIC (Y, E, X, R)
    function deleteEl(el) {
        if (!el || el.getAttribute('data-gone') || el.id === "THE_VOID" || el === executor) return;
        el.setAttribute('data-gone', 'true');
        snappedElements.push(el);
        el.style.transition = '0.4s';
        el.style.transform = 'scale(0) rotate(90deg)';
        setTimeout(() => el.style.visibility = 'hidden', 400);
    }

    const inp = document.getElementById('cmdInp');
    const sug = document.getElementById('sugBox');

    window.addEventListener('keydown', (e) => {
        const k = e.key.toLowerCase();
        
        // Command Panel Toggle
        if (k === '0' && document.activeElement !== inp) {
            e.preventDefault();
            const isOpen = executor.style.transform.includes('scale(1)');
            executor.style.transform = isOpen ? 'translateX(-50%) scale(0)' : 'translateX(-50%) scale(1)';
            if (!isOpen) setTimeout(() => inp.focus(), 100);
        }

        // Abilities
        if (document.activeElement !== inp) {
            if (k === 'y') document.querySelectorAll('p, h1, h2, a, img, span, button, div:not([z-index])').forEach((el, i) => setTimeout(() => deleteEl(el), i * 1));
            if (k === 'e') { snapMode = !snapMode; laser.style.display = snapMode ? 'block' : 'none'; }
            if (k === 'x') { editorMode = !editorMode; document.designMode = editorMode ? "on" : "off"; }
            if (k === 'r') {
                snappedElements.forEach(el => { el.style.visibility = 'visible'; el.style.transform = 'none'; el.removeAttribute('data-gone'); });
                snappedElements = [];
                snapMode = false; editorMode = false; laser.style.display = 'none'; document.designMode = "off";
            }
        }

        // Execute Command
        if (e.key === 'Enter' && document.activeElement === inp) {
            if (inp.value === '/html.exe') launchVirus();
            if (inp.value === '/sword.exe') { swordMode = true; gauntlet.textContent = '🗡️'; }
            if (inp.value === '/destroy.page') document.querySelectorAll('p, h1, div:not([z-index])').forEach(el => deleteEl(el));
            inp.value = ''; executor.style.transform = 'translateX(-50%) scale(0)';
        }
        
        // Tab Suggestion
        if (e.key === 'Tab' && sug.style.display === 'block') { e.preventDefault(); inp.value = inp.dataset.m; sug.style.display = 'none'; }
    }, true);

    // Suggestion Logic
    inp.oninput = () => {
        const m = commands.find(c => c.startsWith(inp.value.toLowerCase()));
        if (inp.value && m) { sug.style.display = 'block'; sug.textContent = "TAB TO AUTO-FILL: " + m; inp.dataset.m = m; }
        else sug.style.display = 'none';
    };

    document.addEventListener('mousemove', (e) => {
        gauntlet.style.left = (e.clientX - 30) + 'px';
        gauntlet.style.top = (e.clientY - 30) + 'px';
        laser.style.left = e.clientX + 'px';
        if (snapMode && !swordMode) deleteEl(document.elementFromPoint(e.clientX, e.clientY));
    });

    window.addEventListener('mousedown', (e) => {
        if (swordMode) deleteEl(document.elementFromPoint(e.clientX, e.clientY));
    });
})();
