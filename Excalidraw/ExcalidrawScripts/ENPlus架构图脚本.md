const ea = ExcalidrawAutomate;
ea.reset();

// --- 样式配置 ---
const BIG_W = 180, BIG_H = 60;
const SML_W = 120, SML_H = 30;
const OFF_X = 40, OFF_Y = 40;
const BLUE = "#4a86e8"; // 原图蓝色

function addMember(title, name, x, y) {
    // 1. 绘制蓝色大矩形（职位）
    const bId = ea.addRect(x, y, BIG_W, BIG_H, {
        backgroundColor: BLUE, 
        fillStyle: "solid", 
        strokeColor: "#333"
    });
    ea.addText(x + 5, y + 10, title, {fontSize: 14, color: "#fff"});

    // 2. 绘制白色小矩形（姓名）- 右下偏移
    const sId = ea.addRect(x + OFF_X, y + OFF_Y, SML_W, SML_H, {
        backgroundColor: "#fff", 
        fillStyle: "solid", 
        strokeColor: "#333"
    });
    ea.addText(x + OFF_X + 5, y + OFF_Y + 5, name || " ", {fontSize: 14, color: "#000"});
    
    return bId; // 返回大框ID用于连线
}

// --- 节点布局 (X, Y 坐标) ---
const md = addMember("Managing Director", "Nick Jenkinson", 500, 0);
const fd = addMember("Finance Director", "Paul Ryan", 500, 150);

const hoq = addMember("Head of Operation and Quality", "Rebecca Stapley", 100, 300);
const hos = addMember("Head of Sales", " ", 500, 300);
const hpp = addMember("Head of Product and Delivery", "Ryan Prakoso", 900, 300);

const lip = addMember("Logistic & Inventory Planner", "Ioan Calin", 0, 480);
const sa  = addMember("Sales Admin", "Sue Jones", 250, 480);
const pmm = addMember("Product Marketing Manager", "Richard Noakes", 600, 480);
const spm = addMember("Software Product Manager", "Lori Ho", 850, 480);
const efa = addMember("Electrical & Firmware Eng", "Roshin Saseendran", 1100, 480);

const pd1 = addMember("Project Deputy - Quality", "Abin Sabu", 900, 650);
const pd2 = addMember("Project Deputy - Project", "Gary Tang", 1150, 650);
const asr = addMember("After-Sales Support", "Andrew Frangieh", 1400, 650);

// --- 连线逻辑 (Sharp 直角折线) ---
const conn = (p, c) => ea.connectObjects(p, c, {strokeSharpness: "sharp", strokeColor: "#333"});

conn(md, fd);
[hoq, hos, hpp].forEach(n => conn(fd, n));
[lip, sa].forEach(n => conn(hoq, n));
[pmm, spm, efa].forEach(n => conn(hpp, n));
[pd1, pd2, asr].forEach(n => conn(efa, n));

ea.create({filename: "EN_Plus_Final_Org"});