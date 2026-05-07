# บทพากย์ภาษาไทยสำหรับสไลด์เปรียบเทียบ OMX vs OMO vs OMC

---

## สไลด์ที่ 1 — เปิดตัว

สวัสดีครับ ยินดีต้อนรับสู่การนำเสนอเปรียบเทียบ AI Agent Orchestration สามตัวหลักในตลาดตอนนี้ ได้แก่ OMX OMO และ OMC ข้อมูลในสไลด์นี้ถูกตรวจสอบความถูกต้องด้วย Tavily Search API แล้วครับ จะพาคุณไปดูที่มาที่ไป จุดเด่น จุดด้อย ข้อผิดพลาดที่พบในข้อมูลทั่วไป และแนวทางการเลือกใช้งาน มาเริ่มกันเลยครับ

---

## สไลด์ที่ 2 — ที่มาที่ไป

มาดูที่มาที่ไปของแต่ละตัวกันครับ OMX หรือ Oh My Codex สร้างโดย Yeachan Heo บน GitHub ใบอนุญาต MIT เริ่มต้นราวมีนาคม 2026 ในเวอร์ชัน 0.10 จุด และเวอร์ชันล่าสุดคือ 0.16 จุด ในเดือนพฤษภาคม 2026 คำขวัญคือเหมือนโอฮ์มายแซด แต่สำหรับ Codex เป็น orchestration layer บน Codex CLI โดยตรงครับ OMO หรือ Oh My OpenAgent เดิมชื่อโอฮ์มายโอพencode สร้างโดย code-yeongyu เริ่มต้นราวธันวาคม 2025 เวอร์ชันล่าสุด 3.17.15 ในเดือนพฤษภาคม 2026 เป็นตัวที่ไม่ล็อคใครไว้ ไม่ใช่แค่ Claude หรือ OpenAI แต่ใช้ได้ทุกค่ายครับ OMC หรือ Oh My Claude decode ก็สร้างโดย Yeachan Heo เช่นกัน เริ่มต้นมกราคม 2026 เป็นการพอร์ตคอนเซ็ปต์ของ OMO มาใช้กับ Claude Code โดยเฉพาะครับ

---

## สไลด์ที่ 3 — OMX คืออะไร

OMX ไม่ได้แทนที่ Codex CLI แต่เป็น orchestration layer ที่ครอบบน Codex CLI โดยตรงครับ จุดเด่นคือ workflow สี่ขั้นตอนตั้งแต่ deep interview ไปจนถึง ralph หรือ team execution มี team runtime ที่ใช้ tmux ร่วมกับ git worktrees ทำให้สามารถสร้าง parallel workers แยกกันทำงานได้ไม่ชนกัน มี persistent memory ในโฟลเดอร์ .omx ที่เก็บแผน บันทึก และความจำ รอดจากการถูกตัด context ของ Codex มี native hooks ผ่านไฟล์ .codex/hooks.json โดยตรง ไม่ต้องพึ่งเครื่องมือนอก มี HUD monitor ที่ใช้คำสั่ง omx hud watch ดูสถานะ real time และมีสามสิบสาม skills รวม thirty six workflow skills สำหรับงานประเภทต่างๆ สิ่งสำคัญคือ execution engine หลักยังเป็น Codex หรือ GPT ส่วน Claude กับ Gemini ใช้ได้แค่ worker รองเท่านั้นครับ

---

## สไลด์ที่ 4 — OMO คืออะไร

OMO คือ multi-model agent orchestration harness สำหรับ OpenCode ที่แปลง agent เดี่ยวให้กลายเป็นทีมพัฒนาที่ ship code ได้จริงครับ มีสิบเอ็ด specialized agents เช่น Sisyphus เป็น orchestrator Hephaestus เป็น deep worker Oracle เป็น architect Librarian ค้นหาเอกสาร Explore สำรวจโค้ดเบส และ Multimodal Looker วิเคราะห์ภาพเสียงวิดีโอ จุดแข็งที่สุดคือ multi-provider แท้จริง ใช้ Claude GPT Gemini Grok MiniMax และ local models ได้พร้อมกันในระบบเดียว มี LSP กับ AST tools ที่ให้ IDE precision ที่ CLI ทั่วไปไม่มี มี IntentGate ที่วิเคราะห์ intent จริงของผู้ใช้ก่อนทำงาน ลดการเข้าใจผิด และยังรองรับ hooks skills MCP ของ Claude Code ecosystem ได้อีกด้วยครับ

---

## สไลด์ที่ 5 — OMC คืออะไร

OMC คือการพอร์ตคอนเซ็ปต์ของ OMO มาใช้กับ Claude Code โดยเฉพาะครับ เน้นที่ LSP integration เต็มรูปแบบ มีสิบเอ็ด tools เช่น hover go to definition find references document symbols diagnostics rename และ code actions รวมถึง ast-grep integration ที่ทำ structural code search และ replace แบบ precision สูง มีเจ็ด slash commands สำเร็จรูป เช่น slash sisyphus slash ultrawork slash deepsearch slash analyze slash plan และ slash review พร้อม magic keywords อย่าง ultrawork search และ analyze ที่เรียก workflow ได้ทันที ติดตั้งผ่าน Claude Code plugin marketplace ได้ และมี model matching อัตโนมัติ โดย Opus ไปทำหน้าที่ architect Sonnet เป็น librarian และ Haiku เป็น explore แต่ข้อควรระวังคือ lock ใน Claude ecosystem อย่างเดียว ไม่สามารถใช้ model ค่ายอื่นได้ครับ

---

## สไลด์ที่ 6 — ตารางเปรียบเทียบ

มาดูตารางเปรียบเทียบข้อเท็จจริงกันครับ ด้านผู้สร้าง OMX และ OMC โดย Yeachan Heo ส่วน OMO โดย code-yeongyu ด้าน base platform OMX ใช้ Codex CLI OMO ใช้ OpenCode และ OMC ใช้ Claude Code ด้านโมเดล OMX ใช้ Codex หรือ GPT เป็นหลัก Claude กับ Gemini เป็น worker รอง OMO ใช้ได้ทุกค่ายพร้อมกัน ส่วน OMC lock เป็น Claude model อย่างเดียว ด้าน specialized agents OMX มีสามสิบสาม prompts กับ thirty six skills OMO มีสิบเอ็ด agents และ OMC มีสิบ agents ที่พอร์ตมาจาก OMO ด้าน multi-agent execution OMX ใช้ tmux กับ git worktrees OMO ใช้ background agents parallel กับ discipline enforcement และ OMC ใช้ team-based บน Claude Code ด้าน LSP OMX ไม่มี OMO และ OMC มีเต็มระบบ ด้าน hooks และ extensibility OMX ใช้ native Codex hooks OMO มีสี่สิบกว่า hooks skills MCPs และ OMC ใช้ Claude Code hooks กับ plugin system ทั้งสามตัวใช้ใบอนุญาต MIT ครับ

---

## สไลด์ที่ 7 — OMX จุดเด่น จุดด้อย

มาดูจุดเด่นและจุดด้อยของ OMX กันครับ จุดเด่นคือ workflow เป็นระบบสี่ขั้นตอน ลดความสับสนในการทำงาน team runtime ด้วย tmux กับ git worktrees ทำ parallel ได้จริงและไม่ชนกัน persistent state ในโฟลเดอร์ .omx รอดจาก context pruning native hooks ผ่าน .codex/hooks.json โดยตรง ไม่ต้องใช้ shim นอก HUD monitor ดูสถานะ real time และไม่แยกจาก Codex CLI ใช้ execution engine หลักตลอด ส่วนจุดด้อยคือ setup overhead สูง planning gate เพิ่มขึ้น งานเล็กๆ อาจช้ากว่า raw Codex ผูกติด Codex CLI evolution เช่นเมื่อ Codex เวอร์ชัน 0.117.0 ลบ custom prompts ต้องแก้ตาม ต้องใช้ tmux ถ้าไม่ชินอาจงง และ agent ไม่หลากหลายเท่า OMO เพราะเน้น Codex เป็นหลักครับ

---

## สไลด์ที่ 8 — OMO จุดเด่น จุดด้อย

OMO มีจุดเด่นที่ multi-model แท้จริง ไม่ lock ใคร ใช้ทุกค่ายพร้อมกันในระบบเดียว มีสิบเอ็ด specialized agents ที่เลือก model ตามจุดเด่นของตัวเอง LSP กับ AST tools ให้ IDE precision ที่ vanilla CLI ไม่มี IntentGate วิเคราะห์ intent จริงก่อนทำงาน Claude Code compatible ใช้ hooks skills MCP ของ Claude ได้ และ discipline enforcement ทำให้ agent ไม่หยุดก่อนเสร็จ ส่วนจุดด้อยคือ complexity สูง ส่วนประกอบเยอะ ต้องเรียนรู้เยอะกว่า พึ่งพา OpenCode ต้องมี OpenCode เป็น base ก่อน และ configuration overhead ต้องตั้งค่า provider หลายตัวในขั้นตอนติดตั้งครับ

---

## สไลด์ที่ 9 — OMC จุดเด่น จุดด้อย

OMC มีจุดเด่นที่ LSP integration เต็มรูปแบบ สิบเอ็ด tools บวก ast-grep precision สูง เจ็ด slash commands สำเร็จรูป พร้อม magic keywords ติดตั้งผ่าน Claude Code plugin marketplace ได้ และ model matching อัตโนมัติ โดย Opus ไป architect Sonnet เป็น librarian และ Haiku เป็น explore ส่วนจุดด้อยคือ lock ใน Claude ecosystem ใช้ได้เฉพาะ Claude Code พึ่งพา Claude Code evolution และ Anthropic เคย mass block third party tools ในเดือนมกราคม 2026 มาแล้ว และ OMC ใหม่กว่า OMO ฟีเจอร์บางส่วนยังตามหลัง OMO เพราะเป็น port มาครับ

---

## สไลด์ที่ 10 — ข้อผิดพลาดที่พบบ่อย

มาดูข้อผิดพลาดที่พบบ่อยในข้อมูลทั่วไปกันครับ ข้อแรก ผิดว่า OMX เน้น System และ Terminal ส่วน OMO กับ OMC เน้น Application Development จริงๆ แล้วทั้งสามตัวเป็น coding agent orchestration tools ทำได้ทั้ง system และ software development ไม่ได้แบ่งชัดเจนตามนั้น ข้อสอง ผิดว่า OMX มี slash session และ slash compact เป็นคำสั่ง chat จริงๆ OMX ใช้ CLI subcommands เช่น omx session ไม่ใช่ slash commands ข้อสาม ผิดว่า Codex CLI ดั้งเดิมแค่เขียนคำสั่งให้ดู ไม่รันคำสั่งได้ จริงๆ Codex CLI มีสาม approval modes คือ suggest auto-edit และ full-auto รันคำสั่งได้มาก่อนแล้ว และข้อสี่ ผิดชื่อ OMC โดยเรียกว่า Oh My Claude ธรรมดา จริงๆ ชื่อเต็มคือ oh-my-claudecode มี repo อื่นที่ใช้ชื่อคล้ายกันด้วยครับ

---

## สไลด์ที่ 11 — เลือกใช้ตัวไหน เมื่อไหร่

แล้วควรเลือกใช้ตัวไหนครับ ถ้าคุณชอบ Codex CLI อยู่แล้ว ต้องการ structure การทำงาน team parallel และ persistent memory แบบไม่ต้องเปลี่ยน tool หลัก และต้องการ HUD monitor ดูสถานะ real time เลือก OMX ครับ ถ้าคุณใช้ OpenCode ต้องการ multi-model ที่ไม่ lock ใคร ต้องการ specialized agents LSP tools และ discipline enforcement และต้องการใช้ hooks skills MCP ของ Claude Code ecosystem ได้ด้วย เลือก OMO ครับ ถ้าคุณใช้ Claude Code เป็นหลัก ต้องการ LSP integration เต็มรูปแบบ slash commands และ magic keywords สำเร็จรูป และติดตั้งผ่าน Claude Code plugin marketplace ได้สะดวก เลือก OMC ครับ

---

## สไลด์ที่ 12 — แหล่งอ้างอิง

แหล่งอ้างอิงหลักของข้อมูลนี้ได้แก่ GitHub ของทั้งสาม repo ได้แก่ Yeachan Heo สแลช oh-my-codex code-yeongyu สแลช oh-my-openagent และ Yeachan Heo สแลช oh-my-claudecode รวมถึง Verdent AI Guide Vibe Coding Hub Review a2a-mcp.org blog LinkedIn comparison post โดย Muhammad Khan และ Nimbalyst ข้อมูลนี้ถูก fact-check ด้วย Tavily Search API ในเดือนพฤษภาคม 2026 ครับ ขอบคุณที่ติดตามรับชมครับ
