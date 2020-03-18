---
title: 編譯器警告 C4600 至 C4799
ms.date: 04/21/2019
f1_keywords:
- C4609
- C4658
- C4671
- C4676
- C4689
- C4695
- C4696
- C4719
- C4720
- C4721
- C4728
- C4732
- C4751
- C4752
- C4755
- C4757
- C4767
- C4770
helpviewer_keywords:
- C4609
- C4658
- C4671
- C4676
- C4689
- C4695
- C4696
- C4719
- C4720
- C4721
- C4728
- C4732
- C4751
- C4752
- C4755
- C4757
- C4767
- C4770
ms.assetid: 22bd4392-f3be-445c-9f23-6126aebac901
ms.openlocfilehash: 638af32b27f8d66086f3a39b74ecd46fdbb4649d
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/17/2020
ms.locfileid: "79438179"
---
# <a name="compiler-warnings-c4600-through-c4799"></a>編譯器警告 C4600 至 C4799

本檔的這一節中的文章說明編譯器所產生的警告訊息子集。

[!INCLUDE[error-boilerplate](../../error-messages/includes/error-boilerplate.md)]

## <a name="warning-messages"></a>警告訊息

|警告|訊息|
|-------------|-------------|
|[編譯器警告（層級1） C4600](../../error-messages/compiler-warnings/compiler-warning-level-1-c4600.md)|#pragma ' 宏名稱 '：必須是有效的非空白字串|
|[編譯器警告（層級1） C4602](compiler-warning-level-1-c4602.md)|#pragma pop_macro： ' 宏名稱 ' 沒有此識別碼的上一個 #pragma push_macro|
|[編譯器警告（層級1） C4603](compiler-warning-level-1-c4603.md)|'*identifier*'：宏未定義，或是定義在使用先行編譯標頭之後不同|
|編譯器警告（層級1） C4604|'*type*'：在原生和 managed 界限之間以傳值方式傳遞引數，需要有效的複製程式。 否則，不會定義執行時間行為|
|編譯器警告（層級1） C4605|在目前的命令列上指定了 '/d*宏*'，但在建立先行編譯標頭檔時未指定|
|[編譯器警告（層級1） C4606](../../error-messages/compiler-warnings/compiler-warning-level-1-c4606.md)|#pragma 警告：已忽略「警告號碼」;程式碼分析警告未與警告層級相關聯|
|[編譯器警告（層級3） C4608](../../error-messages/compiler-warnings/compiler-warning-level-3-c4608.md)|'union_member' 已由初始設定式清單中的等位成員 'union_member' 初始化|
|編譯器警告（層級3，錯誤） C4609|'*type1*' 衍生自型別 '*type2*' 上的預設介面「*介面*」。 針對 '*type1*' 使用不同的預設介面，或中斷基底/衍生關聯性。|
|[編譯器警告（層級4） C4610](../../error-messages/compiler-warnings/compiler-warning-level-4-c4610.md)|無法具現化物件 ' class '-需要使用者定義的構造函式|
|[編譯器警告（層級4） C4611](../../error-messages/compiler-warnings/compiler-warning-level-4-c4611.md)|' function ' 和C++ object 析構之間的互動是不可移植的|
|[編譯器警告（層級1） C4612](compiler-warning-level-1-c4612.md)|Include 檔檔名錯誤|
|[編譯器警告（層級1） C4613](compiler-warning-level-1-c4613.md)|'*symbol*'：無法變更區段的類別|
|[編譯器警告（層級1） C4615](../../error-messages/compiler-warnings/compiler-warning-level-1-c4615.md)|#pragma 警告：不明的使用者警告類型|
|[編譯器警告（層級1） C4616](../../error-messages/compiler-warnings/compiler-warning-level-1-c4616.md)|#pragma 警告：警告編號 ' number ' 不是有效的編譯器警告|
|[編譯器警告（層級1） C4618](../../error-messages/compiler-warnings/compiler-warning-level-1-c4618.md)|pragma 參數包含空字串;已忽略 pragma|
|[編譯器警告（層級3） C4619](../../error-messages/compiler-warnings/compiler-warning-level-3-c4619.md)|#pragma warning: 沒有警告編號 'number'|
|[編譯器警告（層級1） C4620](compiler-warning-level-1-c4620.md)|找不到類型 'type' 後置格式的 'operator ++'，已改用前置格式|
|[編譯器警告（層級1） C4621](../../error-messages/compiler-warnings/compiler-warning-level-1-c4621.md)|找不到類型 ' type ' 的後置格式 ' operator--'，使用前置格式|
|[編譯器警告（層級3） C4622](compiler-warning-level-3-c4622.md)|覆寫在物件檔中建立先行編譯標頭檔時所形成的 debug 資訊： ' file '|
|[編譯器警告（層級4） C4623](../../error-messages/compiler-warnings/compiler-warning-level-4-c4623.md)|' 衍生類別 '：預設的函式已隱含定義為刪除，因為無法存取或刪除基類預設的函式|
|[編譯器警告（層級1） C4624](../../error-messages/compiler-warnings/compiler-warning-level-1-c4624.md)|' 衍生類別 '：析構函式已隱含定義為刪除，因為基類的析構函數無法存取或已刪除|
|[編譯器警告（層級4） C4625](../../error-messages/compiler-warnings/compiler-warning-level-4-c4625.md)|' 衍生類別 '：複製的函式已隱含定義為刪除，因為無法存取或刪除基類複製的構造器|
|[編譯器警告（層級4） C4626](../../error-messages/compiler-warnings/compiler-warning-level-4-c4626.md)|' 衍生類別 '：指派運算子已隱含定義為刪除，因為無法存取或刪除基類指派運算子|
|[編譯器警告（層級1） C4627](../../error-messages/compiler-warnings/compiler-warning-level-1-c4627.md)|'\<識別碼 > '：尋找先行編譯標頭使用時略過|
|[編譯器警告（層級1） C4628](../../error-messages/compiler-warnings/compiler-warning-level-1-c4628.md)|不支援使用 -Ze 的雙拼詞。 字元順序 ' 連詞 ' 未解讀為 '% s ' 的替代 token|
|[編譯器警告（層級4） C4629](compiler-warning-level-4-c4629.md)|使用了雙拼詞，字元順序 'digraph' 被解譯為語彙基元 'char' (如果這不是您想要的，請在兩個字元之間插入一個空格)|
|[編譯器警告（層級1） C4630](../../error-messages/compiler-warnings/compiler-warning-level-1-c4630.md)|' symbol '：成員定義上的 ' extern ' 儲存類別規範不合法|
|編譯器警告（層級2） C4631|MSXML 或 XPath 無法使用，將不會處理 XML 文件註解。 reason|
|[編譯器警告（層級1） C4632](../../error-messages/compiler-warnings/compiler-warning-level-1-c4632.md)|XML 檔批註：檔案拒絕存取：原因|
|[編譯器警告（層級3） C4633](../../error-messages/compiler-warnings/compiler-warning-level-3-c4633.md)|XML 檔批註目標：錯誤：原因|
|[編譯器警告（層級4） C4634](compiler-warning-level-4-c4634.md)|XML 檔批註目標：無法套用：原因|
|[編譯器警告（層級3） C4635](compiler-warning-level-3-c4635.md)|XML 文件註解目標: XML 格式錯誤: 原因|
|[編譯器警告（層級3） C4636](compiler-warning-level-3-c4636.md)|套用至結構的 XML 檔批註：標記需要非空白的 ' attribute ' 屬性。|
|[編譯器警告（層級3和層級4） C4637](compiler-warning-level-3-c4637.md)|XML 檔批註目標： \<包含已捨棄 > 標記。 原因|
|[編譯器警告（層級3） C4638](compiler-warning-level-3-c4638.md)|XML 檔批註目標：參考未知的符號 ' symbol '。|
|[編譯器警告（層級4） C4639](../../error-messages/compiler-warnings/compiler-warning-level-4-c4639.md)|MSXML 錯誤，將不會處理 XML 檔批註。 原因|
|[編譯器警告（層級3） C4640](../../error-messages/compiler-warnings/compiler-warning-level-3-c4640.md)|'instance': 區域靜態物件的建構不是安全執行緒|
|[編譯器警告（層級3） C4641](../../error-messages/compiler-warnings/compiler-warning-level-3-c4641.md)|XML 檔批註具有不明確的交互參考：|
|[編譯器警告（層級3） C4645](compiler-warning-level-3-c4645.md)|使用 __declspec(noreturn) 宣告的函式有傳回的陳述式|
|[編譯器警告（層級3） C4646](compiler-warning-level-3-c4646.md)|使用 __declspec(noreturn) 宣告的函式有非 void 的傳回類型|
|編譯器警告（層級3） C4647|行為變更： __is_pod （*類型*）在舊版本中具有不同的值|
|編譯器警告（層級3） C4648|已忽略標準屬性 ' carries_dependency '|
|編譯器警告（層級3） C4649|屬性會在此內容中忽略|
|[編譯器警告（層級1） C4650](../../error-messages/compiler-warnings/compiler-warning-level-1-c4650.md)|不在先行編譯標頭檔中的調試資訊;只有標頭中的全域符號才可使用|
|[編譯器警告（層級1） C4651](../../error-messages/compiler-warnings/compiler-warning-level-1-c4651.md)|為先行編譯標頭指定的 ' definition '，但不適用於目前的編譯|
|[編譯器警告（層級1） C4652](../../error-messages/compiler-warnings/compiler-warning-level-1-c4652.md)|編譯器選項 ' option ' 與先行編譯標頭檔不一致;目前的命令列選項會覆寫在先行編譯標頭檔中定義的|
|[編譯器警告（層級2） C4653](../../error-messages/compiler-warnings/compiler-warning-level-2-c4653.md)|編譯器選項 ' option ' 與先行編譯標頭檔不一致;已忽略目前的命令列選項|
|編譯器警告（層級4） C4654|包含先行編譯標頭檔的程式碼會被忽略。 將程式碼加入先行編譯標頭檔。|
|[編譯器警告（層級1） C4655](compiler-warning-level-1-c4655.md)|' symbol '：自最新組建之後，變數類型是新的，或在其他地方有不同的定義|
|[編譯器警告（層級1） C4656](../../error-messages/compiler-warnings/compiler-warning-level-1-c4656.md)|' symbol '：資料類型是最新組建之後的新增或變更，或在其他地方有不同的定義|
|[編譯器警告（層級1） C4657](compiler-warning-level-1-c4657.md)|運算式牽涉到自最新組建之後的新資料類型|
|編譯器警告（層級1） C4658|' function '：自最新組建之後，函數原型是新的，或在其他地方宣告為不同的|
|[編譯器警告（層級1） C4659](../../error-messages/compiler-warnings/compiler-warning-level-1-c4659.md)|#pragma ' pragma '：使用保留區段 ' 區段 ' 有未定義的行為，請使用 #pragma 批註（連結器，...）|
|[編譯器警告（層級1） C4661](../../error-messages/compiler-warnings/compiler-warning-level-1-c4661.md)|' identifier '：未提供明確樣板具現化要求的合適定義|
|[編譯器警告（層級1） C4662](compiler-warning-level-1-c4662.md)|明確具現化 (Explicit Instantiation)；樣板類別 'identifier1' 沒有特製化 'identifier2' 用的定義|
|[編譯器警告（層級1） C4667](../../error-messages/compiler-warnings/compiler-warning-level-1-c4667.md)|' function '：未定義符合強制具現化的函式樣板|
|[編譯器警告（層級4） C4668](../../error-messages/compiler-warnings/compiler-warning-level-4-c4668.md)|' symbol ' 未定義為預處理器宏，以 ' 指示詞 ' 的 ' 0 ' 取代|
|[編譯器警告（層級1） C4669](../../error-messages/compiler-warnings/compiler-warning-level-1-c4669.md)|' cast '：不安全的轉換： ' class ' 是 managed 類型物件|
|[編譯器警告（層級4） C4670](compiler-warning-level-4-c4670.md)|' identifier '：無法存取這個基類|
|編譯器警告（層級4） C4671|' identifier '：無法存取複製的構造函式|
|[編譯器警告（層級4） C4672](compiler-warning-level-4-c4672.md)|' identifier1 '：不明確。 第一個看到的當做 'identifier2'|
|[編譯器警告（層級4） C4673](../../error-messages/compiler-warnings/compiler-warning-level-4-c4673.md)|擲回 ' identifier '，將不會在 catch 網站上考慮下列類型|
|[編譯器警告（層級1） C4674](compiler-warning-level-1-c4674.md)|'method' 必須宣告為 'static'，而且只能有一個參數|
|編譯器警告（層級4） C4676|'% s '：無法存取此析構函式|
|[編譯器警告（層級1） C4677](../../error-messages/compiler-warnings/compiler-warning-level-1-c4677.md)|' function '：非私用成員的簽章包含元件私用類型 ' private_type '|
|[編譯器警告（層級1） C4678](compiler-warning-level-1-c4678.md)|基底類別 'base_type' 比 'derived_type' 更難以存取|
|[編譯器警告（層級1） C4679](../../error-messages/compiler-warnings/compiler-warning-level-1-c4679.md)|' member '：無法匯入成員|
|[編譯器警告（層級4） C4680](../../error-messages/compiler-warnings/compiler-warning-level-4-c4680.md)|' class '： coclass 未指定預設介面|
|[編譯器警告（層級4） C4681](compiler-warning-level-4-c4681.md)|' class '： coclass 未指定作為事件來源的預設介面|
|[編譯器警告（層級4） C4682](compiler-warning-level-4-c4682.md)|' parameter '：沒有指定方向參數屬性，預設為 [in]|
|[編譯器警告（層級1） C4683](../../error-messages/compiler-warnings/compiler-warning-level-1-c4683.md)|' function '：事件來源具有 ' out'-參數;在連結多個事件處理常式時，請小心|
|[編譯器警告（層級1） C4684](../../error-messages/compiler-warnings/compiler-warning-level-1-c4684.md)|' attribute '：警告！ 屬性可能會導致不正確程式碼產生：請小心使用|
|[編譯器警告（層級1） C4685](compiler-warning-level-1-c4685.md)|剖析樣板參數時需要 '> >'，但卻找到 '>>'|
|[編譯器警告（層級3） C4686](../../error-messages/compiler-warnings/compiler-warning-level-3-c4686.md)|'user-defined type': 行為可能有變更，在 UDT 傳回呼叫慣例中發生變更|
|[編譯器警告（錯誤） C4687](../../error-messages/compiler-warnings/compiler-warning-c4687.md)|' class '：密封抽象類別無法實作為介面 ' interface '|
|[編譯器警告（層級1） C4688](../../error-messages/compiler-warnings/compiler-warning-level-1-c4688.md)|'constraint': 條件約束清單含有組件私用類型 'type'，將無法由組件外部存取|
|編譯器警告（層級1） C4689|'% c '： #pragma detect_mismatch 中不支援的字元;已忽略 #pragma|
|[編譯器警告（層級4） C4690](../../error-messages/compiler-warnings/compiler-warning-level-4-c4690.md)|\[ emitidl （pop）]：超過推播的 pop 數|
|[編譯器警告（層級1） C4691](../../error-messages/compiler-warnings/compiler-warning-level-1-c4691.md)|' type '：參考的類型必須在未參考的元件 ' file ' 中，但目前的轉譯單位中所定義的類型已改為使用|
|[編譯器警告（層級1） C4692](../../error-messages/compiler-warnings/compiler-warning-level-1-c4692.md)|'function': 非私用成員的簽章含有組件私用原生類型 'native_type'|
|[編譯器警告（層級1，錯誤） C4693](../../error-messages/compiler-warnings/compiler-warning-c4693.md)|' class '：密封抽象類別不能有任何實例成員的實例成員 '|
|[編譯器警告（層級1，錯誤） C4694](../../error-messages/compiler-warnings/compiler-warning-c4694.md)|' class '：密封抽象類別不能有基類 ' base_class '|
|編譯器警告（層級1） C4695|#pragma execution_character_set： ' character set ' 不是支援的引數：目前只支援 ' UTF-8 '|
|編譯器警告（層級1） C4696|/ZBvalue1 選項超出範圍;假設為 ' value2 '|
|[編譯器警告（層級1和層級4） C4700](../../error-messages/compiler-warnings/compiler-warning-level-1-and-level-4-c4700.md)|使用了未初始化的區域變數 ' name '|
|[編譯器警告（層級4） C4701](../../error-messages/compiler-warnings/compiler-warning-level-4-c4701.md)|使用了可能未初始化的本機變數 ' name '|
|[編譯器警告（層級4） C4702](../../error-messages/compiler-warnings/compiler-warning-level-4-c4702.md)|無法連線的程式碼|
|[編譯器警告（層級4） C4703](../../error-messages/compiler-warnings/compiler-warning-level-4-c4703.md)|使用了可能未初始化的本機指標變數 '% s '|
|[編譯器警告（層級4） C4706](../../error-messages/compiler-warnings/compiler-warning-level-4-c4706.md)|條件運算式中的指派|
|[編譯器警告（層級4） C4709](../../error-messages/compiler-warnings/compiler-warning-level-4-c4709.md)|陣列索引運算式中的逗號運算子|
|[編譯器警告（層級4） C4710](../../error-messages/compiler-warnings/compiler-warning-level-4-c4710.md)|'function': 未內嵌函式|
|[編譯器警告（層級1） C4711](../../error-messages/compiler-warnings/compiler-warning-level-1-c4711.md)|為自動內嵌展開選取的函數 ' function '|
|[編譯器警告（層級4） C4714](../../error-messages/compiler-warnings/compiler-warning-level-4-c4714.md)|函式 ' function ' 標記為 __forceinline 不是內嵌的|
|[編譯器警告（層級1） C4715](../../error-messages/compiler-warnings/compiler-warning-level-1-c4715.md)|' function '：並非所有的控制路徑都會傳回值|
|[編譯器警告（層級1，錯誤） C4716](../../error-messages/compiler-warnings/compiler-warning-level-1-c4716.md)|' function '：必須傳回值|
|[編譯器警告（層級1） C4717](../../error-messages/compiler-warnings/compiler-warning-level-1-c4717.md)|' function '：在所有控制路徑上遞迴，函式會造成執行時間堆疊溢位|
|[編譯器警告（層級4） C4718](compiler-warning-level-4-c4718.md)|' 函式呼叫 '：遞迴呼叫沒有副作用，正在刪除|
|編譯器警告（層級1） C4719|指定 Qfast 時，找到 Double 常數-使用 ' f ' 做為後置詞以表示單精確度|
|編譯器警告（層級2） C4720|內嵌組譯工具報告： ' message '|
|編譯器警告（層級1） C4721|' function '：不能當做內建函式使用|
|[編譯器警告（層級1） C4722](compiler-warning-level-1-c4722.md)|' function '：析構函式永遠不會傳回，潛在的記憶體流失|
|[編譯器警告（層級3） C4723](../../error-messages/compiler-warnings/compiler-warning-level-3-c4723.md)|可能除以0|
|[編譯器警告（層級3） C4724](compiler-warning-level-3-c4724.md)|MOD 的模數可能為 0|
|編譯器警告（層級3） C4725|指令在一些 Pentium 上可能不正確|
|[編譯器警告（層級1） C4727](../../error-messages/compiler-warnings/compiler-warning-level-1-c4727.md)|Obj_file_1 和 obj_file_2 中找到具有相同時間戳記且名為 pch_file 的 PCH。  使用第一個 PCH。|
|編譯器警告（層級1） C4728|已忽略/Yl-選項，因為需要 PCH 參考|
|編譯器警告（層級4） C4729|依據 flow graph 產生的警告，發現函式太大|
|[編譯器警告（層級1） C4730](../../error-messages/compiler-warnings/compiler-warning-level-1-c4730.md)編譯器警告（層級1） C4730|' main '：混合 _m64 和浮點運算式可能會導致不正確的程式碼|
|[編譯器警告（層級1） C4731](../../error-messages/compiler-warnings/compiler-warning-level-1-c4731.md)|' 指標 '：內嵌組解碼程式碼修改了框架指標暫存器 ' register '|
|編譯器警告（層級1） C4732|此架構中不支援內建函式 '% s '|
|[編譯器警告（層級1） C4733](../../error-messages/compiler-warnings/compiler-warning-level-1-c4733.md)|內嵌 asm 指派給 ' FS： 0 '：處理常式未註冊為安全處理常式|
|[編譯器警告（層級3） C4738](../../error-messages/compiler-warnings/compiler-warning-level-3-c4738.md)|在記憶體中儲存 32 位元浮點結果，可能會損失效能|
|[編譯器警告（層級1） C4739](compiler-warning-level-1-c4739.md)|變數 'var' 的參考超過了它的儲存空間|
|[編譯器警告（層級4） C4740](../../error-messages/compiler-warnings/compiler-warning-level-4-c4740.md)|傳入或傳出的內嵌 asm 程式碼隱藏了全域優化|
|[編譯器警告（層級1） C4742](../../error-messages/compiler-warnings/compiler-warning-level-1-c4742.md)|' var ' 在 ' file1 ' 和 ' file2 ' 中有不同的對齊方式：數位和數位|
|[編譯器警告（層級1） C4743](../../error-messages/compiler-warnings/compiler-warning-level-1-c4743.md)|' file1 ' 和 ' file2 ' 中的 ' type ' 具有不同的大小：數位和數位位元組|
|[編譯器警告（層級1） C4744](../../error-messages/compiler-warnings/compiler-warning-level-1-c4744.md)|' file1 ' 和 ' file2 ' 中的 ' var ' 類型不同： ' type1 ' 和 ' type2 '|
|[編譯器警告 C4746](../../error-messages/compiler-warnings/compiler-warning-c4746.md)|「*運算式*」的變動性存取受限於/volatile：\<iso&#124;ms > 設定;請考慮使用 __iso_volatile_load/store 內建函式|
|[編譯器警告（層級1） C4747](../../error-messages/compiler-warnings/compiler-warning-level-1-c4747.md)|呼叫受控的 ' entrypoint '： Managed 程式碼可能無法在載入器鎖定下執行，包括 DLL 進入點和從 DLL 進入點到達的呼叫|
|編譯器警告（層級4） C4749|有條件地支援： offsetof 套用至非標準版面配置類型 '*type*'|
|[編譯器警告（層級1） C4750](compiler-warning-level-1-c4750.md)|'identifier': 函式中有 _alloca() 內嵌成迴圈|
|編譯器警告（層級4） C4751|/arch： AVX 不適用於內嵌 ASM 內的 Intel （R） Streaming SIMD Extensions|
|編譯器警告（層級4） C4752|找到 Intel （R）先進向量擴充功能;請考慮使用/arch： AVX|
|[編譯器警告（層級4） C4754](compiler-warning-level-4-c4754.md)|在% s （% d）的比較中，算數運算的轉換規則，表示無法執行一個分支。 將 '% s ' 轉換成 '% s ' （或% d 個位元組的類似類型）。|
|編譯器警告 C4755|在% s （% d）的比較中，算數運算的轉換規則，表示無法在內嵌函式中執行一個分支。 將 '% s ' 轉換成 '% s ' （或% d 個位元組的類似類型）。|
|[編譯器警告（層級2） C4756](../../error-messages/compiler-warnings/compiler-warning-level-2-c4756.md)|常數算術中溢位|
|編譯器警告（層級4） C4757|注標是一個不帶正負號的值，您是否想要負常數？|
|[編譯器警告（層級4） C4764](compiler-warning-level-4-c4764.md)|無法將 catch 物件對齊超過16個位元組|
|編譯器警告（層級4） C4767|區段名稱 '% s ' 長度超過8個字元，且連結器將截斷|
|編譯器警告（層級3） C4768|忽略連結規格之前的 __declspec 屬性|
|編譯器警告 C4770|部分驗證的列舉 '*name*' 做為索引使用|
|編譯器警告 C4771|必須使用簡單的指標來建立界限;已忽略 MPX 內建函式|
|[編譯器警告（層級1，錯誤） C4772](../../error-messages/compiler-warnings/compiler-warning-level-1-c4772.md)|#import 從遺失的類型程式庫參考類型;當做預留位置使用的 ' missing_type '|
|編譯器警告（層級4） C4774|'*字串*'：引數編號中預期的格式字串不是字串常*值*|
|編譯器警告（層級3） C4775|函式 '*function*' 的格式字串 '*string*' 中使用非標準的擴充功能|
|編譯器警告（層級1） C4776|函式 '*function*' 的格式字串中不允許 '%*character*'|
|編譯器警告（層級4） C4777|'*function*'：格式字串 '*string*' 需要類型 '*type1*' 的引數，但 variadic 引數*編號*具有類型 '*type2*'|
|編譯器警告（層級3） C4778|'*function*'：未結束的格式字串 '*string*'|
|[編譯器警告（層級1） C4788](../../error-messages/compiler-warnings/compiler-warning-level-1-c4788.md)|' identifier '：識別碼已截斷為 ' number ' 個字元|
|[編譯器警告（層級1） C4789](../../error-messages/compiler-warnings/compiler-warning-level-1-c4789.md)|大小 N 位元組的緩衝區 'identifier' 會溢位；將從位移 L 開始寫入 M 位元組|
|編譯器警告（層級2） C4792|函式 '% s ' 已使用 sysimport 宣告宣告，並從機器碼參考;需要匯入程式庫|
|[編譯器警告（層級1和3） C4793](../../error-messages/compiler-warnings/compiler-warning-level-1-and-3-c4793.md)|' function '：函式編譯為原生： \ n\t ' reason '|
|[編譯器警告（層級1） C4794](compiler-warning-level-1-c4794.md)|執行緒區域儲存區變數 '% s ' 的區段已從 '% s ' 變更為 '% s '|
|[編譯器警告（層級1） C4799](../../error-messages/compiler-warnings/compiler-warning-level-1-c4799.md)|函數 ' function ' 沒有 EMM 指令|

## <a name="see-also"></a>另請參閱

[C/C++編譯器和組建工具的錯誤和警告](../compiler-errors-1/c-cpp-build-errors.md) \
[編譯器警告 C4000-至 c5999](compiler-warnings-c4000-c5999.md)
