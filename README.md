<html>
  <head>
    <link rel="icon" href="picsart_24-06_2P5-10-56-54-582%20(1).jpg"/>
  </head>
<body>
<style>
  body{
    background-image: url('Picsart_24-05-16_20-56-54-582%20(1).jpg');
  }

</style>


<ul>
  <li><h3>before running your bot must you use this cod in consol or shell if you cant writing on consol"npm install discord.js@12
</h3></li>
 <li><h3>dont forget replace"YOUR_TOKEN_BOT" WITH TOKEN BOT</h3></li>
</ul>
<h2>project file</h2>
<A download href="index (4).js"><h2>download projet file</h2></A>

<table>
  <tr>
    <td>
const express = require('express');
const app = express();
const port = 3000;

app.get('/', (req, res) => res.send('البوت جاهز'));

app.listen(port, () => console.log(`Example app listening at http://localhost:${port}`));

const {Discord, Client, MessageEmbed, MessageActionRow, MessageButton, Modal, TextInputComponent} = require("discord.js")
const client = new Client({intents: 7753})

client.on("ready", async () => {
  console.log(`Logged in as ${client.user.username}!`)
}).login(process.env.token)

const prefix = ""

const replace = [
  {
    word: "سعر",
    replace: "س3ر"
  },
   {
    word: "حساب",
    replace: "ل7ساب"
  },
{
    word: "حسابات",
    replace: "7سابات"
  },

]

client.on("messageCreate", async message => {
  if (message.content.startsWith(prefix + "replacer")) {
  if(!message.member.permissions.has("ADMINISTRATOR")) return;
    const embed = new MessageEmbed()
    .setTitle("تشفير")
    .setDescription("**لتشفير منشورك قم بالضغط على الزر و ضع منشورك.**")
    .setThumbnail(message.guild.iconURL())
    
      const row = new MessageActionRow()
        .addComponents(
            new MessageButton()
            .setStyle("SECONDARY")
            .setLabel("تشفير")
            .setCustomId('replace')
        )
    message.channel.send({embeds: [embed], components: [row]})
  }
})


client.on("interactionCreate", async i => {
  if (!i.isButton()) return;
  if (i.customId == "replace") {
            const modal = new Modal()
            .setTitle('تشفير')
            .setCustomId('rep')

   const replacer = new TextInputComponent()
            .setCustomId('replacetext')
            .setLabel(`قم ب وضع منشورك هنا لتشفيره`)
            .setMaxLength(2000)
            .setRequired(true)
            .setStyle("PARAGRAPH")
    
       const rows = [replacer].map(
                (component) => new MessageActionRow().addComponents(component)
            )
            modal.addComponents(...rows);
            i.showModal(modal);
        
  }
  
})

client.on("interactionCreate", async i => {
  if (!i.isModalSubmit()) return;
  if (i.customId == "rep") {
let text = i.fields.getTextInputValue('replacetext');
    let replaced = false;

    replace.forEach(t => {
      const regex = new RegExp(t.word, 'g');
      if (regex.test(text)) {
        text = text.replace(regex, t.replace);
        replaced = true;
      }
    });


    if (replaced) {
i.reply({content: `\`المنشور بعد التشفير :\`\n\n ${text}`, ephemeral: true})
    } else {
      i.reply({content: "**منشورك لا يحتاج للتشفير**", ephemeral: true})
    }
  }
  
})
process.on("unhandledRejection", e => {
  console.log(e)
})
const mySecret = process.env['token bot']
</td>
  </tr>
</table>
<A href="https://bleu1js.github.io/Blue._.js/"><img src="Picsart_24-05-17_11-16-44-661.jpg"></A>


</body>
</html>
