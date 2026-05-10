# Wingo30s
const axios = require('axios');

const TOKEN = "আপনার_পুরো_JWT_টোকেন_এখানে_বসান"; // আপনি যেটা চ্যাটে দিয়েছেন

async function fetchGameData() {
    try {
        const response = await axios.post('https://draw.ar-lottery01.com/WinGo/WinGo_30S/GetHistoryIssuePage', 
        {
            "pageIndex": 1,
            "pageSize": 10,
            "gameId": 1
        }, 
        {
            headers: {
                'Authorization': `Bearer ${TOKEN}`,
                'Content-Type': 'application/json',
                'User-Agent': 'Mozilla/5.0 (Android 10; Mobile; rv:115.0) Gecko/115.0 Firefox/115.0'
            }
        });

        const data = response.data;
        console.log("Latest Result:", data.data.list[0]);
        // এখানে ফায়ারবেসে সেভ করার কোড যোগ করতে পারেন
    } catch (error) {
        console.error("Data Fetch Failed:", error.message);
    }
}

// প্রতি ৩০ সেকেন্ডে রান হবে
setInterval(fetchGameData, 30000);
