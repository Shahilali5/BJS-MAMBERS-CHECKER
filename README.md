
# Telegram Bot with Join Verification

This repository provides a script to verify users' membership in multiple Telegram channels before granting them access to specific bot functionalities.

---

## ðŸŒŸ Features  
- âœ… Verifies user membership across multiple channels.  
- âš™ï¸ Ensures the bot is an admin in the required channels.  
- âš ï¸ Displays appropriate messages if requirements aren't met.  
- ðŸš€ Easy-to-host and configure for public channels.  

---

## ðŸš€ How to Use  

### Step 1: Host the Script  
Host the provided PHP script on your domain. Make sure the hosting supports PHP.  

### Step 2: Add the Join Command Callback  
Include the following `join` command in your bot's script:  

```javascript
var channels = ["@Shahilwebschat", "@ShahilWebs", "@A1BOTPROMOTER", "@GODMOD57"];  
var channelsString = channels.join(","); // Convert the array to a comma-separated string  

HTTP.get({  
  url: "<your-hosted-domain>/ChatMember.php?bot_token=" + bot.token + "&user_id=" + user.telegramid + "&chat_id=" + channelsString,  
  success: "/check"  
});
```

> **ðŸ”” Note**: Replace the `channels` array with your public channel usernames and `<your-hosted-domain>` with your hosting domain.

---

### Step 3: Handle Verification  
Add the following code to handle the verification result:  

```javascript
if (content) {  
  const { status, is_joined } = JSON.parse(content);  

  if (status === "false") {  
    return Bot.sendMessage("*ðŸ¤– Make your bot an admin in the channel.*");  
  }  

  if (is_joined) {  
    Bot.runCommand("/mainmenu");  
  } else {  
    Bot.sendMessage("*âš ï¸ You need to join all channels.*");  
  }  
}
```

---

## ðŸŽ¨ Styles and Animations  

- Add inline buttons or keyboard animations to guide users through the process.  
- Use bold (`**`) or italic (`*`) text for better visibility.  
- Incorporate emojis to make your messages visually appealing.  

---

## ðŸ“ Requirements  
1. **Public Channels Only**  
   - This script only works with public Telegram channels.  

2. **Bot Admin Rights**  
   - Ensure your bot is an admin in the required channels.  

---

## ðŸ‘¤ Claims  

All claims: [@Shahil440](https://t.me/Shahil440)

---

## ðŸ› ï¸ Example Usage  

Hereâ€™s a styled message example for your bot:  

```javascript
Bot.sendMessage("*Welcome to the Bot!* ðŸŽ‰

To proceed, please join the following channels:
- [Shahil Webs Chat](https://t.me/Shahilwebschat)
- [Shahil Webs](https://t.me/ShahilWebs)

Once joined, click 'Joined âœ…' to continue.");
```

**Sample Inline Button Code:**  
```javascript
Bot.sendInlineKeyboard(
  [
    [{ text: "Joined âœ…", command: "/check" }],
    [{ text: "Help ðŸ†˜", url: "https://t.me/Shahil440" }]
  ],
  "Please confirm your channel membership."
);
```

---

### ðŸ“· Screenshot Example  

- Button animations when clicked  
- Styled messages with emojis  
- Inline buttons for a seamless user experience  

---

Feel free to raise issues or contribute to the repository. ðŸš€
