truecallerSDK.init({
  partnerKey: 'UT4tc13e81273017b4ae9bc426075da5aaaaa',
  requestNonce: 'randomStringForSecurity',
  redirectURI: 'https://CYPHERBOYZz.github.io/verifylookup/callback',
  userData: ['phoneNumber', 'email', 'name'],
  buttonId: 'truecaller-login-button',
  showIfTruecallerAppNotInstalled: true,
  style: {
    theme: 'default',
    shape: 'rectangle',
    borderRadius: '5px'
  }
});

truecallerSDK.onSuccess((response) => {
  const user = response;
  document.getElementById('user-name').textContent = `Name: ${user.name}`;
  document.getElementById('user-phone').textContent = `Phone: ${user.phoneNumber}`;
  document.getElementById('user-email').textContent = `Email: ${user.email || 'N/A'}`;
  document.getElementById('user-info').classList.remove('hidden');
});

truecallerSDK.onError((error) => {
  alert('An error occurred during authentication. Please try again.');
});
