import React, { useState, useMemo } from 'react';
import { Search, User, Building2, Briefcase, Hash, Info, Users, CheckCircle2 } from 'lucide-react';

const App = () => {
  // 整合所有圖片的人員資料 (總計 128 筆)
  const data = [
    // 1-X 系列 (策劃團隊)
    { id: '1-0', group: '典試委員', unit: '國立台灣師範大學', name: '鄭聖敏' },
    { id: '1-1', group: '召集人', unit: '新竹縣政府', name: '蔡淑貞' },
    { id: '1-2', group: '副召集人', unit: '新竹縣政府', name: '沈靜濤' },
    { id: '1-3', group: '總策畫', unit: '新竹縣政府', name: '范貴蟬' },
    { id: '1-4', group: '副策畫', unit: '退休校長', name: '饒忠韻' },
    { id: '1-5', group: '副策畫', unit: '碧潭國小校長', name: '曾道明' },
    { id: '1-6', group: '副策畫', unit: '照門國小校長', name: '田育昆' },
    { id: '1-7', group: '執行策劃', unit: '新竹縣政府', name: '張智翔' },

    // 2-X 系列 (工作組人員 - 勝利國中)
    { id: '2-1', group: '行政組 組長', unit: '勝利國中', name: '徐永明' },
    { id: '2-2', group: '行政組 副組長', unit: '勝利國中', name: '徐韻瑛' },
    { id: '2-3', group: '行政組 組員', unit: '勝利國中', name: '黃郁雯' },
    { id: '2-4', group: '行政組 組員', unit: '勝利國中', name: '陳麗朱' },
    { id: '2-5', group: '行政組 組員', unit: '勝利國中', name: '吳宜靜' },
    { id: '2-6', group: '行政組 組員', unit: '勝利國中', name: '石佳儀' },
    { id: '2-7', group: '行政組 組員', unit: '勝利國中', name: '李明' },
    { id: '2-8', group: '試場佈置組 副組長', unit: '勝利國中', name: '方欣蕙' },
    { id: '2-9', group: '試場佈置組 組員', unit: '勝利國中', name: '陳彥頤' },
    { id: '2-10', group: '試場佈置組 組員', unit: '勝利國中', name: '徐意竹' },
    { id: '2-11', group: '試場佈置組 組員', unit: '勝利國中', name: '余政翰' },
    { id: '2-12', group: '試場佈置組 組員', unit: '勝利國中', name: '林文津' },
    { id: '2-13', group: '試場佈置組 組員', unit: '勝利國中', name: '吳倩如' },
    { id: '2-14', group: '總務組 副組長', unit: '勝利國中', name: '趙端蓉' },
    { id: '2-15', group: '總務組 組員', unit: '勝利國中', name: '柯同洲' },
    { id: '2-16', group: '總務組 組員', unit: '勝利國中', name: '張藍尹' },
    { id: '2-17', group: '總務組 組員', unit: '勝利國中', name: '黃德欽' },
    { id: '2-18', group: '總務組 組員', unit: '勝利國中', name: '吳宥葶' },
    { id: '2-19', group: '總務組 組員', unit: '勝利國中', name: '林瑋力' },
    { id: '2-20', group: '總務組 組員', unit: '勝利國中', name: '劉彧' },
    { id: '2-21', group: '秩序組 副組長', unit: '勝利國中', name: '曾義強' },
    { id: '2-22', group: '秩序組 組員', unit: '勝利國中', name: '莊馥萍' },
    { id: '2-23', group: '秩序組 組員', unit: '勝利國中', name: '廖婉臻' },
    { id: '2-24', group: '秩序組 組員', unit: '勝利國中', name: '郭安婕' },
    { id: '2-25', group: '秩序組 組員', unit: '勝利國中', name: '陳怡均' },
    { id: '2-26', group: '秩序組 組員', unit: '勝利國中', name: '簡惠美' },
    { id: '2-27', group: '秩序組 組員', unit: '勝利國中', name: '林賢威' },
    { id: '2-28', group: '秩序組 組員', unit: '勝利國中', name: '張惠晴' },
    { id: '2-29', group: '秩序組 組員', unit: '勝利國中', name: '陳弘念' },
    { id: '2-30', group: '秩序組 組員', unit: '勝利國中', name: '涂哲宏' },
    { id: '2-31', group: '秩序組 組員', unit: '勝利國中', name: '林冠婷' },
    { id: '2-32', group: '秩序組 組員', unit: '勝利國中', name: '吳巧雯' },
    { id: '2-33', group: '秩序組 組員', unit: '勝利國中', name: '吳佳華' },
    { id: '2-34', group: '秩序組 組員', unit: '勝利國中', name: '曾逸瑤' },
    { id: '2-35', group: '秩序組 組員', unit: '勝利國中', name: '王涵羽' },
    { id: '2-36', group: '會計組 組長', unit: '勝利國中', name: '黃玉雯' },
    { id: '2-37', group: '會計組 副組長', unit: '勝利國中', name: '黃慧茹' },
    { id: '2-38', group: '醫護組 組員', unit: '勝利國中', name: '蔡岫虹' },
    { id: '2-39', group: '醫護組 副組長', unit: '勝利國中', name: '林雨勤' },

    // 3-X 系列 (成功/博愛)
    { id: '3-1', group: '語文組 組長', unit: '成功國中', name: '陳雯玲' },
    { id: '3-2', group: '語文組 副組長', unit: '成功國中', name: '魏瓊玲' },
    { id: '3-3', group: '數理組 組長', unit: '博愛國中', name: '郭雅玲' },
    { id: '3-4', group: '數理組 組長', unit: '博愛國中', name: '施靜泓' },

    // 4-X 系列 (東興/仁愛/自強)
    { id: '4-1', group: '數理組 組長', unit: '東興國中', name: '林健明' },
    { id: '4-2', group: '數理組 副組長', unit: '東興國中', name: '張得歆' },
    { id: '4-3', group: '數理組 組員', unit: '東興國中', name: '劉芷帆' },
    { id: '4-4', group: '數理組 組員', unit: '東興國中', name: '方郁涵' },
    { id: '4-5', group: '數理組 組員', unit: '東興國中', name: '余奕憲' },
    { id: '4-6', group: '數理組 組員', unit: '東興國中', name: '許睿絜' },
    { id: '4-7', group: '數理組 組員', unit: '東興國中', name: '曾靜筠' },
    { id: '4-8', group: '數理組 組員', unit: '東興國中', name: '吳思韻' },
    { id: '4-9', group: '數理組 組長', unit: '仁愛國中', name: '劉安倫' },
    { id: '4-10', group: '數理組 副組長', unit: '仁愛國中', name: '宋美紅' },
    { id: '4-11', group: '數理組 組員', unit: '仁愛國中', name: '蔣忠惠' },
    { id: '4-12', group: '數理組 組員', unit: '仁愛國中', name: '王潔敏' },
    { id: '4-13', group: '數理組 組員', unit: '仁愛國中', name: '曾新容' },
    { id: '4-14', group: '數理組 組員', unit: '仁愛國中', name: '古馨蘭' },
    { id: '4-15', group: '數理組 組員', unit: '仁愛國中', name: '張瑜玲' },
    { id: '4-16', group: '語文組 組長', unit: '自強國中', name: '朱紋秀' },
    { id: '4-17', group: '語文組 副組長', unit: '自強國中', name: '黃友倫' },
    { id: '4-18', group: '語文組 組員', unit: '自強國中', name: '林靜秋' },
    { id: '4-19', group: '語文組 組員', unit: '自強國中', name: '林慧蓉' },

    // 5-X 系列 (數理組監試人員)
    { id: '5-1', group: '數理組 監試人員', unit: '成功國中', name: '賴芊瑜' },
    { id: '5-2', group: '數理組 監試人員', unit: '成功國中', name: '廖源弘' },
    { id: '5-3', group: '數理組 監試人員', unit: '成功國中', name: '張唯坪' },
    { id: '5-4', group: '數理組 監試人員', unit: '成功國中', name: '徐睦賢' },
    { id: '5-5', group: '數理組 監試人員', unit: '成功國中', name: '王天行' },
    { id: '5-6', group: '數理組 監試人員', unit: '成功國中', name: '陳音穎' },
    { id: '5-7', group: '數理組 監試人員', unit: '成功國中', name: '黃伶莉' },
    { id: '5-8', group: '數理組 監試人員', unit: '成功國中', name: '許雲景' },
    { id: '5-9', group: '數理組 監試人員', unit: '成功國中', name: '余欣樺' },
    { id: '5-10', group: '數理組 監試人員', unit: '成功國中', name: '劉庭君' },
    { id: '5-11', group: '數理組 監試人員', unit: '東興國中', name: '吳宗修' },
    { id: '5-12', group: '數理組 監試人員', unit: '東興國中', name: '黃意婷' },
    { id: '5-13', group: '數理組 監試人員', unit: '東興國中', name: '吳立中' },
    { id: '5-14', group: '數理組 監試人員', unit: '東興國中', name: '林弘霖' },
    { id: '5-15', group: '數理組 監試人員', unit: '東興國中', name: '戴嘉瑋' },
    { id: '5-16', group: '數理組 監試人員', unit: '東興國中', name: '洪聖宇' },
    { id: '5-17', group: '數理組 監試人員', unit: '東興國中', name: '卓怡薇' },
    { id: '5-18', group: '數理組 監試人員', unit: '東興國中', name: '王蕙菁' },
    { id: '5-19', group: '數理組 監試人員', unit: '東興國中', name: '李易儒' },
    { id: '5-20', group: '數理組 監試人員', unit: '東興國中', name: '李賜珍' },
    { id: '5-21', group: '數理組 監試人員', unit: '勝利國中', name: '謝筱莉' },
    { id: '5-22', group: '數理組 監試人員', unit: '勝利國中', name: '陳家綺' },
    { id: '5-23', group: '數理組 監試人員', unit: '勝利國中', name: '蔡宛均' },
    { id: '5-24', group: '數理組 監試人員', unit: '勝利國中', name: '李智瑋' },
    { id: '5-25', group: '數理組 監試人員', unit: '勝利國中', name: '劉宛甄' },
    { id: '5-26', group: '數理組 監試人員', unit: '勝利國中', name: '葉琬瑩' },
    { id: '5-27', group: '數理組 監試人員', unit: '仁愛國中', name: '陳惠君' },
    { id: '5-28', group: '數理組 監試人員', unit: '仁愛國中', name: '吳育蓉' },
    { id: '5-29', group: '數理組 監試人員', unit: '仁愛國中', name: '鍾雨真' },
    { id: '5-30', group: '數理組 監試人員', unit: '仁愛國中', name: '黃愛雅' },
    { id: '5-31', group: '數理組 監試人員', unit: '仁愛國中', name: '廖翊岑' },
    { id: '5-32', group: '數理組 監試人員', unit: '博愛國中', name: '陳雅婷' },
    { id: '5-33', group: '數理組 監試人員', unit: '博愛國中', name: '吳榮光' },
    { id: '5-34', group: '數理組 監試人員', unit: '博愛國中', name: '呂英曄' },
    { id: '5-35', group: '數理組 監試人員', unit: '博愛國中', name: '林庭娟' },
    { id: '5-36', group: '數理組 監試人員', unit: '博愛國中', name: '彭怡然' },
    { id: '5-37', group: '數理組 監試人員', unit: '自強國中', name: '蔡鈴珍' },
    { id: '5-38', group: '數理組 監試人員', unit: '自強國中', name: '鄭芬如' },
    { id: '5-39', group: '數理組 監試人員', unit: '自強國中', name: '葉碧桃' },
    { id: '5-40', group: '數理組 監試人員', unit: '自強國中', name: '龔亭仔' },
    { id: '5-41', group: '數理組 監試人員', unit: '自強國中', name: '劉玉婷' },
    { id: '5-42', group: '數理組 監試人員', unit: '文興國中', name: '陳慧君' },
    { id: '5-43', group: '數理組 監試人員', unit: '竹北國中', name: '姜信安' },
    { id: '5-44', group: '數理組 監試人員', unit: '新湖國中', name: '劉康文' },

    // 6-X 系列 (語文組監試人員)
    { id: '6-1', group: '語文組 監試人員', unit: '成功國中', name: '范美瓊' },
    { id: '6-2', group: '語文組 監試人員', unit: '成功國中', name: '周春綢' },
    { id: '6-3', group: '語文組 監試人員', unit: '成功國中', name: '劉華娟' },
    { id: '6-4', group: '語文組 監試人員', unit: '東興國中', name: '張家榮' },
    { id: '6-5', group: '語文組 監試人員', unit: '東興國中', name: '李慧雯' },
    { id: '6-6', group: '語文組 監試人員', unit: '東興國中', name: '鄭凱豪' },
    { id: '6-7', group: '語文組 監試人員', unit: '勝利國中', name: '李美玟' },
    { id: '6-8', group: '語文組 監試人員', unit: '勝利國中', name: '王俐珍' },
    { id: '6-9', group: '語文組 監試人員', unit: '仁愛國中', name: '吳李洋' },
    { id: '6-10', group: '語文組 監試人員', unit: '仁愛國中', name: '蘇萃茹' },
    { id: '6-11', group: '語文組 監試人員', unit: '博愛國中', name: '林思妤' },
    { id: '6-12', group: '語文組 監試人員', unit: '博愛國中', name: '林昱吟' },
    { id: '6-13', group: '語文組 監試人員', unit: '自強國中', name: '陳怡樺' },
    { id: '6-14', group: '語文組 監試人員', unit: '自強國中', name: '詹佳琪' },
  ];

  const [searchTerm, setSearchTerm] = useState('');

  // 搜尋邏輯
  const filteredData = useMemo(() => {
    const term = searchTerm.trim();
    if (!term) return [];
    
    return data.filter(item => 
      item.name.includes(term) || 
      item.id.includes(term) || 
      item.unit.includes(term) ||
      item.group.includes(term)
    );
  }, [searchTerm]);

  return (
    <div className="min-h-screen bg-slate-50 p-4 md:p-8 font-sans text-slate-900 selection:bg-blue-100 selection:text-blue-900">
      <div className="max-w-2xl mx-auto">
        {/* Header */}
        <header className="mb-8 text-center">
          <div className="inline-flex items-center justify-center p-3 bg-white rounded-2xl shadow-sm mb-4">
            <Users className="text-blue-600 h-8 w-8" />
          </div>
          <h1 className="text-3xl font-extrabold text-slate-800 mb-2 tracking-tight">人員編號查詢系統</h1>
          <p className="text-slate-500 font-medium italic">最新資料已匯入：6-X 系列監試名單</p>
        </header>

        {/* Search Bar */}
        <div className="relative mb-10 group">
          <div className="absolute inset-y-0 left-0 pl-5 flex items-center pointer-events-none">
            <Search className="h-6 w-6 text-slate-400 group-focus-within:text-blue-500 transition-colors" />
          </div>
          <input
            type="text"
            className="block w-full pl-14 pr-4 py-5 border-2 border-slate-200 rounded-[2rem] leading-5 bg-white shadow-sm placeholder-slate-300 focus:outline-none focus:ring-8 focus:ring-blue-500/5 focus:border-blue-500 transition-all text-xl"
            placeholder="輸入姓名或單位查詢..."
            value={searchTerm}
            onChange={(e) => setSearchTerm(e.target.value)}
          />
        </div>

        {/* Results Container */}
        <div className="space-y-4">
          {!searchTerm.trim() ? (
            /* 隱藏狀態提示 */
            <div className="text-center py-20 bg-white rounded-[2.5rem] border border-slate-100 shadow-sm transition-all">
              <div className="inline-flex items-center justify-center w-20 h-20 rounded-full bg-blue-50 text-blue-200 mb-6">
                <CheckCircle2 size={44} />
              </div>
              <h3 className="text-slate-600 text-xl font-bold mb-2">請輸入關鍵字</h3>
              <p className="text-slate-400 px-12 leading-relaxed font-medium">系統已備妥 128 位人員資料，輸入姓名即刻查詢您的職務與編號。</p>
            </div>
          ) : filteredData.length > 0 ? (
            /* 顯示搜尋結果 */
            <div className="animate-in fade-in slide-in-from-top-4 duration-500 space-y-4">
              <div className="flex justify-between items-center px-4">
                <p className="text-[10px] font-bold text-slate-400 uppercase tracking-[0.2em]">搜尋結果：共 {filteredData.length} 筆</p>
              </div>
              {filteredData.map((item, index) => (
                <div 
                  key={index} 
                  className="bg-white p-6 rounded-[2rem] shadow-md border-2 border-transparent hover:border-blue-100 hover:shadow-xl hover:shadow-blue-900/5 transition-all group overflow-hidden"
                >
                  <div className="flex flex-col md:flex-row md:items-center justify-between gap-6">
                    <div className="flex items-center gap-5">
                      <div className="h-16 w-16 rounded-2xl bg-gradient-to-br from-blue-600 to-indigo-700 flex-shrink-0 flex items-center justify-center text-white shadow-lg group-hover:rotate-2 transition-transform">
                        <User size={32} />
                      </div>
                      <div>
                        <h2 className="text-2xl font-black text-slate-800 tracking-tight">{item.name}</h2>
                        <div className="flex items-center gap-1.5 text-slate-500 mt-1 font-semibold">
                          <Building2 size={16} className="text-indigo-400" />
                          <span>{item.unit}</span>
                        </div>
                      </div>
                    </div>
                    
                    <div className="grid grid-cols-2 md:flex gap-8 border-t md:border-t-0 pt-5 md:pt-0">
                      <div className="flex flex-col">
                        <span className="text-[10px] font-bold text-blue-500 uppercase tracking-widest mb-1">人員編號</span>
                        <div className="flex items-center gap-1 text-slate-900 font-black text-3xl">
                          <Hash size={24} className="text-blue-500" />
                          <span>{item.id}</span>
                        </div>
                      </div>
                      <div className="flex flex-col min-w-[140px]">
                        <span className="text-[10px] font-bold text-slate-400 uppercase tracking-widest mb-1">工作組別</span>
                        <div className="flex items-center gap-1.5 text-slate-700 font-bold bg-slate-50 px-3 py-2 rounded-xl border border-slate-100 mt-1 shadow-inner">
                          <Briefcase size={14} className="text-slate-400" />
                          <span className="text-xs">{item.group}</span>
                        </div>
                      </div>
                    </div>
                  </div>
                </div>
              ))}
            </div>
          ) : (
            /* 無結果提示 */
            <div className="text-center py-16 bg-white rounded-[2.5rem] border border-dashed border-red-200">
              <p className="text-red-500 font-bold text-lg mb-1">查無此人</p>
              <p className="text-slate-400 text-sm">請確認姓名輸入是否正確，或嘗試輸入單位關鍵字。</p>
            </div>
          )}
        </div>

        {/* Footer Statistics */}
        <footer className="mt-16 text-center text-slate-400 pb-12">
          <div className="flex flex-wrap justify-center gap-2 mb-6 opacity-60">
            {['1-X', '2-X', '3-X', '4-X', '5-X', '6-X'].map(cat => (
              <span key={cat} className="px-3 py-1 bg-slate-200 rounded-lg text-[9px] font-black text-slate-600">{cat} 系列完成匯入</span>
            ))}
          </div>
          <p className="text-sm font-bold text-slate-500">當前資料庫共計：128 位工作人員</p>
          <p className="text-[10px] mt-2 tracking-widest uppercase font-bold opacity-30">© 2024 Staff Identity Management System</p>
        </footer>
      </div>
    </div>
  );
};

export default App;
