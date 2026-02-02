<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Chat Animation Video</title>

<!-- ================= CSS ================= -->
    <style>
    *{
        margin:0;
        padding:0;
        box-sizing:border-box;
        font-family: Arial, Helvetica, sans-serif;
    }

    body{
        background:black;
        display:flex;
        justify-content:center;
        align-items:center;
        height:100vh;
    }

    /* 9:16 Video Frame */
    .video{
        width:360px;
        height:640px;
        background:linear-gradient(180deg,#111,#1f1f1f);
        border-radius:20px;
        padding:20px;
        overflow:hidden;
    }

    /* Chat container */
    .chat{
        display:flex;
        flex-direction:column;
        gap:12px;
    }

    /* Message base */
    .msg{
        max-width:75%;
        padding:12px 14px;
        font-size:15px;
        border-radius:14px;
        opacity:0;
        transform:translateY(20px);
        animation:show 0.6s forwards;
    }

    /* Left message */
    .left{
        background:#2c2c2c;
        color:white;
        align-self:flex-start;
    }

    /* Right message */
    .right{
        background:#e50914;
        color:white;
        align-self:flex-end;
    }

    /* Animation */
    @keyframes show{
        to{
            opacity:1;
            transform:translateY(0);
        }
    }

    /* Typing indicator */
    .typing{
        width:60px;
        background:#2c2c2c;
        padding:10px;
        border-radius:14px;
        display:flex;
        gap:6px;
        align-self:flex-start;
    }

    .dot{
        width:6px;
        height:6px;
        background:#aaa;
        border-radius:50%;
        animation:blink 1.4s infinite both;
    }

    .dot:nth-child(2){animation-delay:.2s;}
    .dot:nth-child(3){animation-delay:.4s;}

    @keyframes blink{
        0%{opacity:.2;}
        20%{opacity:1;}
        100%{opacity:.2;}
    }
    </style>
    </head>

    <body>

    <div class="video">
        <div class="chat" id="chat"></div>
    </div>

<!-- ================= JAVASCRIPT ================= -->
<script>
const chat = document.getElementById("chat");

const messages = [
    { text: "Bro, did you finish the video edit?", side: "left" },
    { text: "Almost done 🔥", side: "right" },
    { text: "Deadline is today!", side: "left" },
    { text: "Relax 😎 exporting now", side: "right" }
];

let delay = 0;

messages.forEach(msg => {
    setTimeout(() => {

        // typing animation
        const typing = document.createElement("div");
        typing.className = "typing";
        typing.innerHTML = `
            <div class="dot"></div>
            <div class="dot"></div>
            <div class="dot"></div>
        `;
        chat.appendChild(typing);

        setTimeout(() => {
            typing.remove();

            const message = document.createElement("div");
            message.className = `msg ${msg.side}`;
            message.innerText = msg.text;
            chat.appendChild(message);

        }, 900);

    }, delay);

    delay += 1600;
});
</script>

</body>
</html>
