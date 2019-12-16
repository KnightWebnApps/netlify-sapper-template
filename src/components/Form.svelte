<script>
    let formData = {
        name : '',
        email: '',
        message: ''
    };

      const encode = (data) => {
    return Object.keys(data)
        .map(key => encodeURIComponent(key) + "=" + encodeURIComponent(data[key]))
        .join("&");
  }

  function handleSubmit(e) {
      e.preventDefault();
      fetch("/", {
        method: "POST",
        headers: { "Content-Type": "application/x-www-form-urlencoded" },
        body: encode({ "form-name": "contact", ...formData })
      })
        .then(() => alert("Success!"))
        .catch(error => alert(error));

    };
</script>

<form name="contact" method="POST" data-netlify="true">
    <label>Your Name</label>   
    <input type="text" name="name" />
    <label>Your Email</label>
    <input type="email" name="email" />
    <label>Message: </label>
    <textarea name="message"></textarea>
    <button type="submit">Send</button>
</form>