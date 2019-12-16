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

<form on:submit={handleSubmit} action="POST" name="contact" data-netlify="true">
    <input type="hidden" name="form-name" value="contact" />
    <label for="name">Name</label>
    <input 
        name='name' 
        placeholder="Full Name Here" 
        type="text"
        bind:value={formData.name}
    >
    <label for="email">Email</label>
    <input 
        name='email'
        placeholder="Enter Email Address Here"
        type="email"
        bind:value={formData.email}
    >
    <label for="message">Message</label>
    <input 
        name='message'
        placeholder="Enter Message Here"
        type="message"
        bind:value={formData.message}
    >
    <button type="submit"> Submit </button>
</form>