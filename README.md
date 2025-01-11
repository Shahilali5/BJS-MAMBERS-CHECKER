
# Telegram Bot with Join Verification

This repository provides a script to verify users' membership in multiple Telegram channels before granting them access to specific bot functionalities.

---

## 🌟 Features  
- ✅ Verifies user membership across multiple channels.  
- ⚙️ Ensures the bot is an admin in the required channels.  
- ⚠️ Displays appropriate messages if requirements aren't met.  
- 🚀 Easy-to-host and configure for public channels.  

---

## 🚀 How to Use  

### Step 1: Host the Script  
Host the provided PHP script on your domain. Make sure the hosting supports PHP.  

### Step 2: Add the Join Command Callback  
Include the following `join` command in your bot's script:  

```javascript
var channels = ["@Shahilwebschat", "@ShahilWebs", "@A1BOTPROMOTER", "@GODMOD57"];  
var channelsString = channels.join(","); // Convert the array to a comma-separated string  

HTTP.get({  
  url: "<your-hosted-domain>/getChatMember.php?bot_token=" + bot.token + "&user_id=" + user.telegramid + "&chat_id=" + channelsString,  
  success: "/check"  
});
```

> **🔔 Note**: Replace the `channels` array with your public channel usernames and `<your-hosted-domain>` with your hosting domain.

---

### Step 3: Handle Verification  
Add the following code to handle the verification result:  

```javascript
if (content) {  
  const { status, is_joined } = JSON.parse(content);  

  if (status === "false") {  
    return Bot.sendMessage("*🤖 Make your bot an admin in the channel.*");  
  }  

  if (is_joined) {  
    Bot.runCommand("/mainmenu");  
  } else {  
    Bot.sendMessage("*⚠️ You need to join all channels.*");  
  }  
}
```

---

---

## 📝 Requirements  
1. **Public Channels Only**  
   - This script only works with public Telegram channels.  

2. **Bot Admin Rights**  
   - Ensure your bot is an admin in the required channels.  

---

## 👤 Claims  

All claims: [@Shahil440](https://t.me/Shahil440)

---

## 🛠️ Example Usage  

Here’s a styled message example for your bot:  

```javascript
Bot.sendMessage("*Welcome to the Bot!* 🎉

To proceed, please join the following channels:
- [Shahil Webs Chat](https://t.me/Shahilwebschat)
- [Shahil Webs](https://t.me/ShahilWebs)

Once joined, click 'Joined ✅' to continue.");
```

**Sample Inline Button Code:**  
```javascript
Bot.sendInlineKeyboard(
  [
    [{ text: "Joined ✅", command: "/join" }],
    [{ text: "Help 🆘", url: "https://t.me/Shahil440" }]
  ],
  "Please confirm your channel membership."
);
```

---

### 📷 Screenshot Example  

- Button animations when clicked  
- Styled messages with emojis  
- Inline buttons for a seamless user experience  

---

Feel free to raise issues or contribute to the repository. 🚀
