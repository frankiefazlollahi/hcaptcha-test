<body>

    <div>Open the console!</div>
    
    <!--    <script src="https://cdn.jsdelivr.net/npm/vanilla-hcaptcha" async defer></script>-->
    <script src="/node_modules/vanilla-hcaptcha/dist/index.min.js"></script>
    
    <h-captcha id="signupCaptcha"
               site-key="ce694ef0-dbaa-4334-a531-0ad28fabb361"
               host="https://hcaptcha-heroku.herokuapp.com"
               size="normal"
               theme="dark"
               tabindex="0"></h-captcha>
    
    <button on:click={executeHCaptcha}>EXECUTE</button>
    <button on:click={resetHCaptcha}>RESET</button>
    
    <script>
        const signupCaptcha = document.getElementById('signupCaptcha');
    
        signupCaptcha.addEventListener('loaded', () => {
            console.log('hCaptcha Component Loaded');
            // Safe to call `execute` once component is loaded
            // signupCaptcha.execute();
        });
        signupCaptcha.addEventListener('verified', (e) => {
            console.log('verified event', { token: e.token, eKey: e.eKey });
        });
        signupCaptcha.addEventListener('expired', () => {
            console.log('expired event');
        });
        signupCaptcha.addEventListener('error', (e) => {
            console.log('error event', { error: e.error });
        });
    
        function executeHCaptcha() {
            signupCaptcha.execute();
        }
    
        function resetHCaptcha() {
            signupCaptcha.reset();
        }
    </script>
</body>