<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>سجل الفنون البصرية - تصميم البطاقات المطور الذكي</title>
    
    <script src="https://cdn.tailwindcss.com"></script>
    <link href="https://fonts.googleapis.com/css2?family=Alexandria:wght@300;400;500;600;700;800;900&family=Cairo:wght@400;600;700;800&display=swap" rel="stylesheet">
    
    <style>
        :root {
            --art-accent: #4f46e5;
            --art-accent-light: #e0e7ff;
            --art-gradient: linear-gradient(135deg, #4f46e5 0%, #7c3aed 100%);
            --text-dark: #0f172a;
            --text-gray: #475569;
            --bg-workspace: #f1f5f9;
            --name-font-size: 1rem;
        }

        body { 
            font-family: 'Cairo', sans-serif; 
            background-color: var(--bg-workspace); 
            color: var(--text-dark);
            margin: 0; 
            padding-top: 90px;
            padding-bottom: 40px;
            -webkit-print-color-adjust: exact !important;
            print-color-adjust: exact !important;
            background-image: radial-gradient(#cbd5e1 1px, transparent 1px);
            background-size: 24px 24px;
        }

        .heading-font { font-family: 'Alexandria', sans-serif; }

        .a4-page {
            width: 210mm; 
            height: 297mm; 
            background: #ffffff; 
            margin: 0 auto 30px auto; 
            padding: 12mm 10mm; 
            box-shadow: 0 25px 50px -12px rgba(0,0,0,0.15);
            border-radius: 16px;
            position: relative; 
            display: flex; 
            flex-direction: column;
            box-sizing: border-box;
            page-break-after: always;
            border: 2px solid #e0e7ff;
            overflow: hidden; 
        }
        
        .a4-page:last-child { page-break-after: auto; margin-bottom: 0; }

        .header-banner {
            display: flex; justify-content: space-between; align-items: center;
            border-bottom: 3px solid #e2e8f0; padding-bottom: 12px; margin-bottom: 15px; position: relative;
        }

        .header-banner::after {
            content: ''; position: absolute; bottom: -3px; left: 0; width: 30%; height: 3px; background: var(--art-gradient);
        }

        .title-group h1 { font-size: 1.4rem; font-weight: 900; color: var(--text-dark); margin: 0 0 6px 0; }
        .tags-row { display: flex; gap: 8px; flex-wrap: wrap; }
        .tag-badge { background: #f8fafc; padding: 4px 10px; border-radius: 6px; font-size: 0.75rem; font-weight: 800; border: 1px solid #cbd5e1; }

        .week-indicator { background: var(--art-gradient); color: white; padding: 10px 20px; border-radius: 12px; text-align: center; }
        .week-indicator .w-name { font-family: 'Alexandria', sans-serif; font-size: 1rem; font-weight: 900; }
        .week-indicator .w-dates { font-size: 0.7rem; font-weight: 700; margin-top: 2px; }

        .cards-table { width: 100%; border-collapse: separate; border-spacing: 0 6px; margin-top: 0; flex-grow: 1; }
        
        .cards-table thead th { color: var(--text-gray); font-size: 0.75rem; font-weight: 800; padding: 2px 4px; text-align: center; }
        .cards-table thead .th-name { text-align: right; padding-right: 15px; }

        .cards-table tbody tr { background-color: #ffffff; transition: all 0.2s; }
        
        .cards-table td {
            height: 52px;
            padding: 4px 6px; text-align: center; vertical-align: middle;
            border-top: 1.5px solid #e2e8f0; border-bottom: 1.5px solid #e2e8f0;
        }
        
        .cards-table td:first-child { border-right: 4px solid var(--art-accent); border-top-right-radius: 8px; border-bottom-right-radius: 8px; }
        .cards-table td:last-child { border-left: 1.5px solid #e2e8f0; border-top-left-radius: 8px; border-bottom-left-radius: 8px; }
        .cards-table td.col-day { border-left: 1px solid #f1f5f9; }
        .cards-table td.col-percent { border-right: 1px dashed #cbd5e1; }

        .cards-table tbody tr:nth-child(3n+1) td:first-child { border-right-color: #4f46e5; }
        .cards-table tbody tr:nth-child(3n+2) td:first-child { border-right-color: #0ea5e9; }
        .cards-table tbody tr:nth-child(3n+3) td:first-child { border-right-color: #f43f5e; }

        .cards-table td.col-day:nth-child(3) { background-color: rgba(79, 70, 229, 0.02); }
        .cards-table td.col-day:nth-child(4) { background-color: rgba(14, 165, 233, 0.02); }
        .cards-table td.col-day:nth-child(5) { background-color: rgba(16, 185, 129, 0.02); }
        .cards-table td.col-day:nth-child(6) { background-color: rgba(245, 158, 11, 0.02); }
        .cards-table td.col-day:nth-child(7) { background-color: rgba(244, 63, 94, 0.02); }

        .cards-table th:nth-child(3) .day-header-card { border-top: 3px solid #4f46e5; }
        .cards-table th:nth-child(4) .day-header-card { border-top: 3px solid #0ea5e9; }
        .cards-table th:nth-child(5) .day-header-card { border-top: 3px solid #10b981; }
        .cards-table th:nth-child(6) .day-header-card { border-top: 3px solid #f59e0b; }
        .cards-table th:nth-child(7) .day-header-card { border-top: 3px solid #f43f5e; }

        .col-idx { width: 30px; font-weight: 900; color: #94a3b8; font-size: 0.9rem;}
        .col-name { text-align: right !important; font-weight: 800; width: 32%; padding-right: 10px !important; font-size: var(--name-font-size); }
        .col-day { width: 10%; }
        .col-percent { width: 12%; font-weight: 800; }

        .attendance-split { display: flex; justify-content: center; gap: 4px; }

        .check-box {
            width: 22px; height: 22px;
            border-radius: 4px; border: 1.5px solid #cbd5e1;
            display: flex; align-items: center; justify-content: center;
            font-size: 0.65rem; font-weight: 900; color: #94a3b8;
            cursor: pointer; transition: all 0.2s; background: #f8fafc;
        }

        .check-box:hover { border-color: #94a3b8; }
        .check-box.active-p { background: #10b981 !important; border-color: #059669 !important; color: white !important; }
        .check-box.active-a { background: #f43f5e !important; border-color: #e11d48 !important; color: white !important; }

        /* نظام التصغير التلقائي (Auto-Scaling) */
        .scale-1 .cards-table td { height: 42px; padding: 2px 4px; }
        .scale-1 .cards-table { border-spacing: 0 4px; }
        
        .scale-2 .cards-table td { height: 35px; padding: 1px 4px; }
        .scale-2 .cards-table { border-spacing: 0 3px; }
        .scale-2 .check-box { width: 18px; height: 18px; font-size: 0.6rem; }
        .scale-2 .col-name div { font-size: calc(var(--name-font-size) * 0.9); }
        .scale-2 .day-header-card { padding: 4px 2px !important; }
        
        .scale-3 .cards-table td { height: 28px; padding: 0px 4px; }
        .scale-3 .cards-table { border-spacing: 0 2px; }
        .scale-3 .check-box { width: 16px; height: 16px; font-size: 0.55rem; border-width: 1px;}
        .scale-3 .col-name div { font-size: calc(var(--name-font-size) * 0.85); }
        .scale-3 .header-banner { margin-bottom: 8px; padding-bottom: 8px; }
        .scale-3 .title-group h1 { font-size: 1.2rem; }
        .scale-3 .day-header-card { padding: 2px 1px !important; }

        .footer-stats {
            margin-top: auto; padding: 10px 15px;
            background: #f8fafc; border: 1px solid #e2e8f0; border-radius: 12px;
            display: flex; justify-content: space-between; align-items: center;
        }

        [contenteditable="true"] { outline: none; transition: all 0.2s; border-radius: 4px; padding: 1px 4px; border: 1px dashed transparent; }
        [contenteditable="true"]:hover { background-color: #f1f5f9; border-color: #cbd5e1; }
        [contenteditable="true"]:focus { background-color: #ffffff; border-color: var(--art-accent); border-style: solid;}

        .btn-delete { color: #ef4444; cursor: pointer; font-size: 14px; opacity: 0; transition: opacity 0.2s; position: absolute; right: -8px; top: 50%; transform: translateY(-50%); }
        tr:hover .btn-delete { opacity: 1; }

        .glass-nav {
            background: rgba(255, 255, 255, 0.95); backdrop-filter: blur(8px);
            border-bottom: 1px solid #e2e8f0; box-shadow: 0 4px 15px rgba(0,0,0,0.05);
            position: fixed; top: 0; left: 0; right: 0; z-index: 100;
            padding: 10px 20px; display: flex; justify-content: space-between; align-items: center; flex-wrap: wrap; gap: 10px;
        }

        @media print {
            @page { size: A4 portrait !important; margin: 0 !important; }
            html, body { background: #ffffff !important; margin: 0 !important; padding: 0 !important; width: 210mm !important; }
            .no-print, .glass-nav { display: none !important; }
            
            .a4-page { 
                width: 210mm !important; height: 297mm !important;
                margin: 0 !important; padding: 12mm 10mm !important; 
                box-shadow: none !important; border-radius: 0 !important;
                border: none !important; page-break-after: always !important; 
            }
            .btn-delete { display: none !important; }
            .col-percent, .th-percent { display: none !important; }
            .cards-table td.col-day:nth-child(7) { border-left: 1.5px solid #e2e8f0 !important; border-top-left-radius: 8px !important; border-bottom-left-radius: 8px !important; }
            [contenteditable="true"] { border: none !important; padding: 0 !important; background: transparent !important; }
            
            .cards-table th:nth-child(3) .day-header-card { background: linear-gradient(180deg, rgba(79, 70, 229, 0.01) 0%, rgba(255,255,255,1) 100%) !important; }
            .cards-table th:nth-child(4) .day-header-card { background: linear-gradient(180deg, rgba(14, 165, 233, 0.01) 0%, rgba(255,255,255,1) 100%) !important; }
            .cards-table th:nth-child(5) .day-header-card { background: linear-gradient(180deg, rgba(16, 185, 129, 0.01) 0%, rgba(255,255,255,1) 100%) !important; }
            .cards-table th:nth-child(6) .day-header-card { background: linear-gradient(180deg, rgba(245, 158, 11, 0.01) 0%, rgba(255,255,255,1) 100%) !important; }
            .cards-table th:nth-child(7) .day-header-card { background: linear-gradient(180deg, rgba(244, 63, 94, 0.01) 0%, rgba(255,255,255,1) 100%) !important; }
        }
    </style>
</head>
<body>

    <div class="glass-nav no-print">
        <div class="flex items-center gap-2">
            <div class="bg-indigo-600 text-white p-2 rounded-lg text-lg shadow-md">🎨</div>
            <div>
                <h2 class="heading-font font-black text-slate-800 text-sm">سجل الفنون البصرية</h2>
                <span class="text-[0.6rem] text-indigo-600 font-bold uppercase">Pro Auto-Scale Edition</span>
            </div>
        </div>

        <div class="flex items-center gap-2 flex-wrap">
            <div class="flex bg-slate-100 rounded-lg p-0.5 border border-slate-200">
                <button onclick="app.changeFontSize(0.1)" class="px-2 py-1 bg-white text-slate-700 rounded text-xs font-bold shadow-sm">A+</button>
                <button onclick="app.changeFontSize(-0.1)" class="px-2 py-1 bg-white text-slate-700 rounded text-xs font-bold shadow-sm ml-0.5">A-</button>
            </div>

            <select id="weekSelector" onchange="app.changeWeek()" class="bg-slate-100 text-slate-900 text-xs font-bold outline-none rounded-lg px-2 py-1.5 border border-slate-200 cursor-pointer"></select>

            <button onclick="app.addStudent()" class="px-3 py-1.5 bg-indigo-50 text-indigo-700 rounded-lg text-xs font-bold hover:bg-indigo-100 transition">➕ إضافة طالب</button>
            <button onclick="app.calculatePercentages()" class="px-3 py-1.5 bg-emerald-50 text-emerald-700 rounded-lg text-xs font-bold hover:bg-emerald-100 transition">📊 حساب النسبة</button>
            
            <div class="h-5 w-px bg-slate-300 mx-1"></div>

            <button onclick="app.exportData()" class="px-2 py-1.5 bg-slate-100 text-slate-700 rounded-lg text-xs font-bold hover:bg-slate-200" title="تصدير نسخة احتياطية">💾</button>
            <label class="px-2 py-1.5 bg-slate-100 text-slate-700 rounded-lg text-xs font-bold hover:bg-slate-200 cursor-pointer" title="استرجاع نسخة احتياطية">
                📥 <input type="file" class="hidden" accept=".json" onchange="app.importData(event)">
            </label>

            <button onclick="app.handlePrint()" class="px-4 py-1.5 bg-slate-900 text-white rounded-lg text-xs font-bold hover:bg-black transition shadow-md heading-font">🖨️ طباعة</button>
            <button onclick="app.clearData()" class="px-2 py-1.5 bg-rose-50 text-rose-600 rounded-lg text-xs font-bold hover:bg-rose-100" title="ضبط المصنع">⚠️</button>
        </div>
    </div>

    <main id="paperContainer"></main>

    <script>
        const app = {
            semesterSchedule: [
                { id: 1, label: "الأسبوع الأول", startDay: 23, startMonth: 8, startYear: 2026 },
                { id: 2, label: "الأسبوع الثاني", startDay: 30, startMonth: 8, startYear: 2026 },
                { id: 3, label: "الأسبوع الثالث", startDay: 6, startMonth: 9, startYear: 2026 },
                { id: 4, label: "الأسبوع الرابع", startDay: 13, startMonth: 9, startYear: 2026 },
                { id: 5, label: "الأسبوع الخامس", startDay: 20, startMonth: 9, startYear: 2026 },
                { id: 6, label: "الأسبوع السادس", startDay: 27, startMonth: 9, startYear: 2026 },
                { id: 7, label: "الأسبوع السابع", startDay: 4, startMonth: 10, startYear: 2026 },
                { id: 8, label: "الأسبوع الثامن", startDay: 11, startMonth: 10, startYear: 2026 },
                { id: 9, label: "الأسبوع التاسع", startDay: 18, startMonth: 10, startYear: 2026 },
                { id: 10, label: "الأسبوع العاشر", startDay: 25, startMonth: 10, startYear: 2026 },
                { id: 11, label: "الأسبوع الحادي عشر", startDay: 1, startMonth: 11, startYear: 2026 },
                { id: 12, label: "الأسبوع الثاني عشر", startDay: 8, startMonth: 11, startYear: 2026 },
                { id: 13, label: "الأسبوع الثالث عشر", startDay: 15, startMonth: 11, startYear: 2026 },
                { id: 14, label: "الأسبوع الرابع عشر", startDay: 29, startMonth: 11, startYear: 2026 },
                { id: 15, label: "الأسبوع الخامس عشر", startDay: 6, startMonth: 12, startYear: 2026 },
                { id: 16, label: "الأسبوع السادس عشر", startDay: 13, startMonth: 12, startYear: 2026 },
                { id: 17, label: "الأسبوع السابع عشر", startDay: 20, startMonth: 12, startYear: 2026 },
                { id: 18, label: "الأسبوع الثامن عشر", startDay: 27, startMonth: 12, startYear: 2026 },
                { id: 19, label: "الأسبوع التاسع عشر", startDay: 3, startMonth: 1, startYear: 2027 }
            ],

            KEY_DATA: 'Art_Data_V7',
            KEY_SET: 'Art_Set_V7',
            KEY_CUSTOM_WEEKS: 'Art_Weeks_V7',
            
            currentWeek: 1,
            students: [],
            settings: {},
            weeksCustom: {},
            currentFontSize: 1.0,
            MAX_PER_PAGE: 20,

            generateDates(day, month, year) {
                let current = new Date(year, month - 1, day);
                let days = [];
                for (let i = 0; i < 5; i++) {
                    let d = new Date(current);
                    d.setDate(current.getDate() + i);
                    days.push(`${d.getDate()}/${d.getMonth() + 1}`);
                }
                return days;
            },

            init() {
                const s = localStorage.getItem(this.KEY_SET);
                const d = localStorage.getItem(this.KEY_DATA);
                const w = localStorage.getItem(this.KEY_CUSTOM_WEEKS);

                this.settings = s ? JSON.parse(s) : {
                    docTitle: "سجل متابعة الحضور والغياب - الفنون البصرية",
                    gradeTitle: "الصف الأول المتوسط (أ)",
                    termTitle: "الفصل الدراسي الأول",
                    yearTitle: "العام 1448هـ",
                    colIdx: "#", colName: "اسم الطالب", colPercent: "النسبة %"
                };

                this.weeksCustom = w ? JSON.parse(w) : {};

                if (d) {
                    this.students = JSON.parse(d);
                } else {
                    this.students = Array.from({length: 12}, (_, i) => ({ id: i+1, name: `طالب افتراضي ${i+1}`, attendance: {}, percentage: "" }));
                }

                this.populateWeekSelector();
                this.renderCurrentView();
            },

            populateWeekSelector() {
                const select = document.getElementById('weekSelector');
                select.innerHTML = '';
                this.semesterSchedule.forEach(w => {
                    const custom = this.weeksCustom[w.id] || {};
                    const label = custom.label || w.label;
                    const opt = document.createElement('option');
                    opt.value = w.id; opt.text = label;
                    if (w.id === this.currentWeek) opt.selected = true;
                    select.appendChild(opt);
                });
            },

            changeWeek() {
                this.currentWeek = parseInt(document.getElementById('weekSelector').value);
                this.renderCurrentView();
            },

            changeFontSize(delta) {
                this.currentFontSize += delta;
                if(this.currentFontSize < 0.7) this.currentFontSize = 0.7;
                if(this.currentFontSize > 1.3) this.currentFontSize = 1.3;
                document.documentElement.style.setProperty('--name-font-size', `${this.currentFontSize}rem`);
            },

            addStudent() {
                this.students.push({ id: Date.now(), name: `طالب جديد`, attendance: {}, percentage: "" });
                this.saveData();
                this.renderCurrentView();
            },

            removeStudent(idx) {
                if(confirm("تأكيد الحذف؟")) {
                    this.students.splice(idx, 1);
                    this.saveData();
                    this.renderCurrentView();
                }
            },

            toggleStatus(sIdx, dIdx, type, el) {
                if(!this.students[sIdx].attendance[this.currentWeek]) {
                    this.students[sIdx].attendance[this.currentWeek] = [null,null,null,null,null];
                }
                const current = this.students[sIdx].attendance[this.currentWeek][dIdx];
                this.students[sIdx].attendance[this.currentWeek][dIdx] = (current === type) ? null : type;
                this.saveData();
                
                const parent = el.parentElement;
                parent.children[0].classList.remove('active-p');
                parent.children[1].classList.remove('active-a');
                if(this.students[sIdx].attendance[this.currentWeek][dIdx] === 'present') parent.children[0].classList.add('active-p');
                if(this.students[sIdx].attendance[this.currentWeek][dIdx] === 'absent') parent.children[1].classList.add('active-a');
                
                this.renderCurrentView(); 
            },

            calculatePercentages() {
                this.students.forEach(s => {
                    let p = 0, t = 0;
                    Object.values(s.attendance).forEach(w => {
                        if(Array.isArray(w)) w.forEach(st => { if(st==='present') p++; if(st) t++; });
                    });
                    s.percentage = t > 0 ? Math.round((p/t)*100)+"%" : "-";
                });
                this.saveData();
                this.renderCurrentView();
            },

            saveData() {
                localStorage.setItem(this.KEY_DATA, JSON.stringify(this.students));
            },

            saveSetting(key, val) {
                this.settings[key] = val;
                localStorage.setItem(this.KEY_SET, JSON.stringify(this.settings));
            },

            saveName(idx, val) {
                this.students[idx].name = val;
                this.saveData();
            },

            saveWeekCustom(weekId, key, val) {
                if(!this.weeksCustom[weekId]) this.weeksCustom[weekId] = {};
                this.weeksCustom[weekId][key] = val.trim();
                localStorage.setItem(this.KEY_CUSTOM_WEEKS, JSON.stringify(this.weeksCustom));
                if(key === 'label') this.populateWeekSelector();
            },

            saveDayName(weekId, dayIdx, val) {
                if(!this.weeksCustom[weekId]) this.weeksCustom[weekId] = {};
                if(!this.weeksCustom[weekId].dayNames) this.weeksCustom[weekId].dayNames = ['الأحد', 'الإثنين', 'الثلاثاء', 'الأربعاء', 'الخميس'];
                this.weeksCustom[weekId].dayNames[dayIdx] = val.trim();
                localStorage.setItem(this.KEY_CUSTOM_WEEKS, JSON.stringify(this.weeksCustom));
            },

            saveDayDate(weekId, dayIdx, val) {
                if(!this.weeksCustom[weekId]) this.weeksCustom[weekId] = {};
                if(!this.weeksCustom[weekId].days) {
                    const w = this.semesterSchedule.find(ww => ww.id === weekId);
                    this.weeksCustom[weekId].days = this.generateDates(w.startDay, w.startMonth, w.startYear);
                }
                this.weeksCustom[weekId].days[dayIdx] = val.trim();
                localStorage.setItem(this.KEY_CUSTOM_WEEKS, JSON.stringify(this.weeksCustom));
            },

            clearData() {
                if(confirm("مسح كافة البيانات والعودة للوضع الافتراضي؟ (12 طالب)")) {
                    localStorage.removeItem(this.KEY_DATA);
                    localStorage.removeItem(this.KEY_SET);
                    localStorage.removeItem(this.KEY_CUSTOM_WEEKS);
                    this.init();
                }
            },

            exportData() {
                const dataStr = JSON.stringify({ students: this.students, settings: this.settings, weeksCustom: this.weeksCustom });
                const blob = new Blob([dataStr], { type: "application/json" });
                const url = URL.createObjectURL(blob);
                const a = document.createElement('a');
                a.href = url; a.download = `سجل_الفنون_${new Date().toLocaleDateString('en-GB').replace(/\//g, '-')}.json`;
                a.click();
            },

            importData(event) {
                const file = event.target.files[0];
                if(file) {
                    const reader = new FileReader();
                    reader.onload = (e) => {
                        try {
                            const parsed = JSON.parse(e.target.result);
                            if(parsed.students) {
                                this.students = parsed.students;
                                this.settings = parsed.settings || this.settings;
                                this.weeksCustom = parsed.weeksCustom || {};
                                this.saveData();
                                localStorage.setItem(this.KEY_SET, JSON.stringify(this.settings));
                                localStorage.setItem(this.KEY_CUSTOM_WEEKS, JSON.stringify(this.weeksCustom));
                                this.renderCurrentView();
                                alert('تم استرجاع البيانات بنجاح!');
                            }
                        } catch(err) { alert('ملف غير صالح!'); }
                    };
                    reader.readAsText(file);
                }
            },

            handlePrint() { window.print(); },

            renderCurrentView() {
                const container = document.getElementById('paperContainer');
                const weekInfo = this.semesterSchedule.find(w => w.id === this.currentWeek);
                
                // جلب التواريخ المخصصة[cite: 1]
                const customWeek = this.weeksCustom[this.currentWeek] || {};
                const defaultDates = this.generateDates(weekInfo.startDay, weekInfo.startMonth, weekInfo.startYear);
                const defaultDayNames = ['الأحد', 'الإثنين', 'الثلاثاء', 'الأربعاء', 'الخميس'];
                
                const weekLabel = customWeek.label || weekInfo.label;
                const weekDatesRange = customWeek.range || `${defaultDates[0]} - ${defaultDates[4]}`;
                const dates = customWeek.days || defaultDates;
                const dayNames = customWeek.dayNames || defaultDayNames;

                let totalRows = Math.max(this.students.length, 12);
                let html = '';
                
                for (let pageStart = 0; pageStart < totalRows; pageStart += this.MAX_PER_PAGE) {
                    let rowsOnThisPage = Math.min(totalRows - pageStart, this.MAX_PER_PAGE);
                    
                    let scaleClass = '';
                    if (rowsOnThisPage > 18) scaleClass = 'scale-3';
                    else if (rowsOnThisPage > 15) scaleClass = 'scale-2';
                    else if (rowsOnThisPage > 12) scaleClass = 'scale-1';

                    html += `
                    <div class="a4-page ${scaleClass}">
                        <div class="header-banner">
                            <div class="title-group">
                                <h1 contenteditable="true" onblur="app.saveSetting('docTitle', this.innerText)">${this.settings.docTitle}</h1>
                                <div class="tags-row">
                                    <span class="tag-badge" contenteditable="true" onblur="app.saveSetting('gradeTitle', this.innerText)">${this.settings.gradeTitle}</span>
                                    <span class="tag-badge" contenteditable="true" onblur="app.saveSetting('termTitle', this.innerText)">${this.settings.termTitle}</span>
                                </div>
                            </div>
                            <div class="week-indicator">
                                <div class="w-name" contenteditable="true" onblur="app.saveWeekCustom(${this.currentWeek}, 'label', this.innerText)">${weekLabel}</div>
                                <div class="w-dates" contenteditable="true" onblur="app.saveWeekCustom(${this.currentWeek}, 'range', this.innerText)" dir="ltr">${weekDatesRange}</div>
                            </div>
                        </div>

                        <table class="cards-table">
                            <thead>
                                <tr>
                                    <th class="col-idx"><span contenteditable="true" onblur="app.saveSetting('colIdx', this.innerText)">${this.settings.colIdx}</span></th>
                                    <th class="col-name th-name"><span contenteditable="true" onblur="app.saveSetting('colName', this.innerText)">${this.settings.colName}</span></th>
                                    ${dayNames.map((name, i) => `
                                        <th class="col-day pb-1">
                                            <div class="day-header-card bg-white border border-slate-200/90 rounded-xl py-1.5 px-1 mx-1 flex flex-col items-center justify-center transition-all hover:bg-slate-50">
                                                <div class="heading-font text-slate-800 font-black text-[0.8rem]" contenteditable="true" onblur="app.saveDayName(${this.currentWeek}, ${i}, this.innerText)">${name}</div>
                                                <div class="text-[0.62rem] font-sans font-bold text-slate-500 mt-1 bg-slate-50 border border-slate-200/70 px-1 py-0.5 rounded shadow-2xs w-max" contenteditable="true" onblur="app.saveDayDate(${this.currentWeek}, ${i}, this.innerText)" dir="ltr">${dates[i]}</div>
                                            </div>
                                        </th>
                                    `).join('')}
                                    <th class="col-percent"><span contenteditable="true" onblur="app.saveSetting('colPercent', this.innerText)">${this.settings.colPercent}</span></th>
                                </tr>
                            </thead>
                            <tbody>
                    `;

                    let pagePresent = 0, pageAbsent = 0, pageActive = 0;

                    for (let i = 0; i < rowsOnThisPage; i++) {
                        const globalIdx = pageStart + i;
                        const student = this.students[globalIdx];
                        const hasStudent = !!student;
                        
                        let sName = hasStudent ? student.name : '';
                        let sPercent = hasStudent ? student.percentage : '';
                        
                        let daysHTML = '';
                        for(let d=0; d<5; d++) {
                            let status = null;
                            if(hasStudent) {
                                if(!student.attendance[this.currentWeek]) student.attendance[this.currentWeek] = [null,null,null,null,null];
                                status = student.attendance[this.currentWeek][d];
                                if(status === 'present') pagePresent++;
                                if(status === 'absent') pageAbsent++; 
                            }
                            daysHTML += `
                                <td class="col-day">
                                    ${hasStudent ? `
                                    <div class="attendance-split">
                                        <div class="check-box ${status === 'present' ? 'active-p' : ''}" onclick="app.toggleStatus(${globalIdx},${d}, 'present', this)">ح</div>
                                        <div class="check-box ${status === 'absent' ? 'active-a' : ''}" onclick="app.toggleStatus(${globalIdx},${d}, 'absent', this)">غ</div>
                                    </div>` : ''}
                                </td>
                            `;
                        }

                        if(hasStudent && sName.trim() !== '') pageActive++;

                        html += `
                            <tr>
                                <td class="col-idx relative">
                                    ${hasStudent ? `<span class="no-print btn-delete" onclick="app.removeStudent(${globalIdx})">&times;</span>` : ''}
                                    ${globalIdx + 1}
                                </td>
                                <td class="col-name"><div contenteditable="true" oninput="app.saveName(${globalIdx}, this.innerText)">${sName}</div></td>
                                ${daysHTML}
                                <td class="col-percent text-xs font-bold text-slate-500">${sPercent}</td>
                            </tr>
                        `;
                    }

                    html += `
                            </tbody>
                        </table>
                        
                        <div class="footer-stats">
                            <div class="flex gap-4">
                                <span class="bg-indigo-50 text-indigo-700 px-3 py-1 rounded-lg text-xs font-bold">👥 طلاب الورقة: ${pageActive}</span>
                                <span class="bg-emerald-50 text-emerald-700 px-3 py-1 rounded-lg text-xs font-bold">✅ حضور: ${pagePresent}</span>
                                <span class="bg-rose-50 text-rose-700 px-3 py-1 rounded-lg text-xs font-bold">❌ غياب: ${pageAbsent}</span>
                            </div>
                        </div>
                    </div>
                    `;
                }

                container.innerHTML = html;
            }
        };

        window.onload = () => app.init();
    </script>
</body>
</html>
