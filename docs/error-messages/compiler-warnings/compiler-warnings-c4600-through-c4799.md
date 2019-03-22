---
title: 編譯器警告 C4600 到 C4799
ms.date: 07/03/2018
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
- C4728"
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
- C4728"
- C4732
- C4751
- C4752
- C4755
- C4757
- C4767
- C4770
ms.assetid: 22bd4392-f3be-445c-9f23-6126aebac901
ms.openlocfilehash: d1b1e06d3a2be71d6386554c704c547c6f2a4672
ms.sourcegitcommit: c1f646c8b72f330fa8cf5ddb0f8f261ba10d16f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/21/2019
ms.locfileid: "58328370"
---
# <a name="compiler-warnings-c4600-through-c4799"></a>編譯器警告 C4600 到 C4799

文件的本節文章會說明編譯器所產生的警告訊息的子集。

[!INCLUDE[error-boilerplate](../../error-messages/includes/error-boilerplate.md)]

## <a name="warning-messages"></a>警告訊息

|警告|訊息|
|-------------|-------------|
|[編譯器警告 (層級 1) C4600](../../error-messages/compiler-warnings/compiler-warning-level-1-c4600.md)|#pragma '巨集名稱': 必須是有效的非空白字串|
|[編譯器警告 （層級 1） C4602](compiler-warning-level-1-c4602.md)|#pragma pop_macro: '巨集名稱' #pragma push_macro，此識別項|
|[編譯器警告 （層級 1） C4603](compiler-warning-level-1-c4603.md)|'*識別碼*': 未定義巨集，或使用先行編譯標頭之後，定義是不同|
|編譯器警告 （層級 1） C4604|'*型別*': 跨越原生與 managed 界限以值傳遞引數需要有效的複製建構函式。 否則執行階段行為未定義|
|編譯器警告 （層級 1） C4605|'/D*巨集*' 在目前的命令列上指定，但未指定建置先行編譯標頭時|
|[編譯器警告 (層級 1) C4606](../../error-messages/compiler-warnings/compiler-warning-level-1-c4606.md)|#pragma 警告： 警告編號' 忽略;程式碼分析警告未與警告層級相關聯|
|[編譯器警告 (層級 3) C4608](../../error-messages/compiler-warnings/compiler-warning-level-3-c4608.md)|'union_member' 已由初始設定式清單中的等位成員 'union_member' 初始化|
|編譯器警告 （層級 3，錯誤） C4609|'*type1*'衍生自預設介面'*介面*'type' 上*type2*'。 使用不同的預設介面 '*type1*'，或中斷基底/衍生關聯性。|
|[編譯器警告 (層級 4) C4610](../../error-messages/compiler-warnings/compiler-warning-level-4-c4610.md)|'class' 可以永遠不會被具現化物件-使用者定義的所需的建構函式|
|[編譯器警告 (層級 4) C4611](../../error-messages/compiler-warnings/compiler-warning-level-4-c4611.md)|'function' 和 c + + 物件解構間的互動是不可移植|
|[編譯器警告 （層級 1） C4612](compiler-warning-level-1-c4612.md)|Include 檔檔名錯誤|
|[編譯器警告 （層級 1） C4613](compiler-warning-level-1-c4613.md)|'*符號*': 無法變更區段類別|
|[編譯器警告 (層級 1) C4615](../../error-messages/compiler-warnings/compiler-warning-level-1-c4615.md)|#pragma 警告： 未知的使用者警告類型|
|[編譯器警告 (層級 1) C4616](../../error-messages/compiler-warnings/compiler-warning-level-1-c4616.md)|#pragma 警告： 警告編號 '數字' 不是有效的編譯器警告|
|[編譯器警告 (層級 1) C4618](../../error-messages/compiler-warnings/compiler-warning-level-1-c4618.md)|pragma 參數包含空白的字串;已忽略 pragma|
|[編譯器警告 (層級 3) C4619](../../error-messages/compiler-warnings/compiler-warning-level-3-c4619.md)|#pragma warning: 沒有警告編號 'number'|
|[編譯器警告 （層級 1） C4620](compiler-warning-level-1-c4620.md)|找不到類型 'type' 後置格式的 'operator ++'，已改用前置格式|
|[編譯器警告 (層級 1) C4621](../../error-messages/compiler-warnings/compiler-warning-level-1-c4621.md)|任何的後置格式的 'operator--' 找到類型 'type'，改用前置格式|
|[編譯器警告 （層級 3） C4622](compiler-warning-level-3-c4622.md)|覆寫偵錯資訊建立期間形成的目的檔中先行編譯標頭: 'file'|
|[編譯器警告 (層級 4) C4623](../../error-messages/compiler-warnings/compiler-warning-level-4-c4623.md)|'derived class': 預設建構函式已隱含定義為刪除，因為基底類別預設建構函式無法存取或已刪除|
|[編譯器警告 (層級 1) C4624](../../error-messages/compiler-warnings/compiler-warning-level-1-c4624.md)|'derived class': 解構函式已隱含定義為刪除，因為基底類別解構函式無法存取或已刪除|
|[編譯器警告 (層級 4) C4625](../../error-messages/compiler-warnings/compiler-warning-level-4-c4625.md)|'derived class': 複製建構函式已隱含定義為刪除，因為基底類別複製建構函式無法存取或已刪除|
|[編譯器警告 (層級 4) C4626](../../error-messages/compiler-warnings/compiler-warning-level-4-c4626.md)|'derived class': 指派運算子已隱含定義為刪除，因為基底類別指派運算子是無法存取或已刪除|
|[編譯器警告 (層級 1) C4627](../../error-messages/compiler-warnings/compiler-warning-level-1-c4627.md)|'\<識別項 >': 尋找先行編譯標頭檔使用時，略過|
|[編譯器警告 (層級 1) C4628](../../error-messages/compiler-warnings/compiler-warning-level-1-c4628.md)|不支援使用 -Ze 的雙拼詞。 字元順序 'digraph' 沒有解譯為 '%s' 的替代 token|
|[編譯器警告 （層級 4） C4629](compiler-warning-level-4-c4629.md)|使用了雙拼詞，字元順序 'digraph' 被解譯為語彙基元 'char' (如果這不是您想要的，請在兩個字元之間插入一個空格)|
|[編譯器警告 (層級 1) C4630](../../error-messages/compiler-warnings/compiler-warning-level-1-c4630.md)|'symbol': 'extern' 儲存類別規範不合法成員定義|
|編譯器警告 （層級 2） C4631|MSXML 或 XPath 無法使用，將不會處理 XML 文件註解。 原因|
|[編譯器警告 (層級 1) C4632](../../error-messages/compiler-warnings/compiler-warning-level-1-c4632.md)|XML 文件註解： 檔案-拒絕存取： 原因|
|[編譯器警告 (層級 3) C4633](../../error-messages/compiler-warnings/compiler-warning-level-3-c4633.md)|XML 文件註解目標： 錯誤： 原因|
|[編譯器警告 （層級 4） C4634](compiler-warning-level-4-c4634.md)|XML 文件註解目標： 無法套用： 原因|
|[編譯器警告 （層級 3） C4635](compiler-warning-level-3-c4635.md)|XML 文件註解目標: XML 格式錯誤: 原因|
|[編譯器警告 （層級 3） C4636](compiler-warning-level-3-c4636.md)|套用至建構的 XML 文件註解： 標記必須是非空白 'attribute' 屬性。|
|[編譯器警告 （層級 3 和層級 4） C4637](compiler-warning-level-3-c4637.md)|XML 文件註解目標：\<包含 > 捨棄的標籤。 原因|
|[編譯器警告 （層級 3） C4638](compiler-warning-level-3-c4638.md)|XML 文件註解目標： 未知符號 'symbol' 參考。|
|[編譯器警告 (層級 4) C4639](../../error-messages/compiler-warnings/compiler-warning-level-4-c4639.md)|MSXML 錯誤，將不會處理註解的 XML 文件。 原因|
|[編譯器警告 (層級 3) C4640](../../error-messages/compiler-warnings/compiler-warning-level-3-c4640.md)|'instance': 區域靜態物件的建構不是安全執行緒|
|[編譯器警告 (層級 3) C4641](../../error-messages/compiler-warnings/compiler-warning-level-3-c4641.md)|XML 文件註解有模稜兩可的交互參考：|
|[編譯器警告 （層級 3） C4645](compiler-warning-level-3-c4645.md)|使用 __declspec(noreturn) 宣告的函式有傳回的陳述式|
|[編譯器警告 （層級 3） C4646](compiler-warning-level-3-c4646.md)|使用 __declspec(noreturn) 宣告的函式有非 void 的傳回類型|
|編譯器警告 （層級 3） C4647|行為變更： __is_pod (*型別*) 之前的版本會有不同的值|
|編譯器警告 （層級 3） C4648|已忽略標準屬性 'carries_dependency'|
|編譯器警告 （層級 3） C4649|在此內容中會忽略屬性|
|[編譯器警告 (層級 1) C4650](../../error-messages/compiler-warnings/compiler-warning-level-1-c4650.md)|不在先行編譯標頭; 中的偵錯資訊只有全域符號標頭中的會提供|
|[編譯器警告 (層級 1) C4651](../../error-messages/compiler-warnings/compiler-warning-level-1-c4651.md)|[定義] 指定先行編譯標頭，但不適用於目前的編譯|
|[編譯器警告 (層級 1) C4652](../../error-messages/compiler-warnings/compiler-warning-level-1-c4652.md)|編譯器選項 'option' 與先行編譯標頭; 不一致目前的命令列選項會覆寫先行編譯標頭中定義|
|[編譯器警告 (層級 2) C4653](../../error-messages/compiler-warnings/compiler-warning-level-2-c4653.md)|編譯器選項 'option' 與先行編譯標頭; 不一致忽略目前的命令列選項|
|編譯器警告 （層級 4） C4654|放在之前的程式碼包含先行編譯標頭行都會被忽略。 您可以將程式碼加入先行編譯標頭。|
|[編譯器警告 （層級 1） C4655](compiler-warning-level-1-c4655.md)|'symbol': 變數類型有新推出的最新的組建，或其他處有不同定義|
|[編譯器警告 (層級 1) C4656](../../error-messages/compiler-warnings/compiler-warning-level-1-c4656.md)|'symbol': 資料類型的新或最新的組建之後已經變更或其他處有不同定義|
|[編譯器警告 （層級 1） C4657](compiler-warning-level-1-c4657.md)|運算式包含自上次組建之後才新增的資料類型|
|編譯器警告 （層級 1） C4658|'function': 函式原型是新推出的最新的組建，或其他處有不同的宣告|
|[編譯器警告 (層級 1) C4659](../../error-messages/compiler-warnings/compiler-warning-level-1-c4659.md)|#pragma 'pragma': 使用保留的區段 'segment' 有未定義的行為，請使用 #pragma 註解 (linker，...)|
|[編譯器警告 (層級 1) C4661](../../error-messages/compiler-warnings/compiler-warning-level-1-c4661.md)|'identifier': 不提供明確樣板具現化要求的合適定義|
|[編譯器警告 （層級 1） C4662](compiler-warning-level-1-c4662.md)|明確具現化 (Explicit Instantiation)；樣板類別 'identifier1' 沒有特製化 'identifier2' 用的定義|
|[編譯器警告 (層級 1) C4667](../../error-messages/compiler-warnings/compiler-warning-level-1-c4667.md)|'function': 沒有函式樣板定義符合強制具現化|
|[編譯器警告 (層級 4) C4668](../../error-messages/compiler-warnings/compiler-warning-level-4-c4668.md)|'symbol' 未定義成前置處理器巨集，以 '0' 取代 '指示詞'|
|[編譯器警告 (層級 1) C4669](../../error-messages/compiler-warnings/compiler-warning-level-1-c4669.md)|'cast': 不安全的轉換: 'class' 是 managed 的類型的物件|
|[編譯器警告 （層級 4） C4670](compiler-warning-level-4-c4670.md)|'identifier': 此基底類別是無法存取|
|編譯器警告 （層級 4） C4671|'identifier': 複製建構函式是無法存取|
|[編譯器警告 （層級 4） C4672](compiler-warning-level-4-c4672.md)|'identifier1': 模稜兩可。 第一個看到的當做 'identifier2'|
|[編譯器警告 (層級 4) C4673](../../error-messages/compiler-warnings/compiler-warning-level-4-c4673.md)|下列類型時擲回 'identifier' 不會考慮使用時，接收站台|
|[編譯器警告 （層級 1） C4674](compiler-warning-level-1-c4674.md)|'method' 必須宣告為 'static'，而且只能有一個參數|
|編譯器警告 （層級 4） C4676|'%s'： 解構函式是無法存取|
|[編譯器警告 (層級 1) C4677](../../error-messages/compiler-warnings/compiler-warning-level-1-c4677.md)|'function': 非私用成員簽章含有組件私用類型 'private_type'|
|[編譯器警告 （層級 1） C4678](compiler-warning-level-1-c4678.md)|基底類別 'base_type' 比 'derived_type' 更難以存取|
|[編譯器警告 (層級 1) C4679](../../error-messages/compiler-warnings/compiler-warning-level-1-c4679.md)|'member': 無法匯入成員|
|[編譯器警告 (層級 4) C4680](../../error-messages/compiler-warnings/compiler-warning-level-4-c4680.md)|'class': coclass 不指定的預設介面。|
|[編譯器警告 （層級 4） C4681](compiler-warning-level-4-c4681.md)|'class': coclass 不指定為事件來源的預設介面|
|[編譯器警告 （層級 4） C4682](compiler-warning-level-4-c4682.md)|'parameter': 沒有方向參數屬性指定，預設為 [in]|
|[編譯器警告 (層級 1) C4683](../../error-messages/compiler-warnings/compiler-warning-level-1-c4683.md)|'function': 事件來源有 'out'-參數;連結多個事件處理常式時請小心|
|[編譯器警告 (層級 1) C4684](../../error-messages/compiler-warnings/compiler-warning-level-1-c4684.md)|' attribute':警告!! 屬性可能造成無效的程式碼產生： 請小心使用|
|[編譯器警告 （層級 1） C4685](compiler-warning-level-1-c4685.md)|剖析樣板參數時需要 '> >'，但卻找到 '>>'|
|[編譯器警告 (層級 3) C4686](../../error-messages/compiler-warnings/compiler-warning-level-3-c4686.md)|'user-defined type': 行為可能有變更，在 UDT 傳回呼叫慣例中發生變更|
|[編譯器警告 （錯誤） C4687](../../error-messages/compiler-warnings/compiler-warning-c4687.md)|'class': 密封抽象類別無法實作介面 'interface'|
|[編譯器警告 （層級 1） C4688](../../error-messages/compiler-warnings/compiler-warning-level-1-c4688.md)|'constraint': 條件約束清單含有組件私用類型 'type'，將無法由組件外部存取|
|編譯器警告 （層級 1） C4689|'%c'： 不支援在 #pragma detect_mismatch; 中的字元忽略 #pragma|
|[編譯器警告 （層級 4） C4690](../../error-messages/compiler-warnings/compiler-warning-level-4-c4690.md)|\[ emitidl (pop)]: pop 數目比 push|
|[編譯器警告 (層級 1) C4691](../../error-messages/compiler-warnings/compiler-warning-level-1-c4691.md)|'type': 未參考組件 'file'，改用目前的轉譯單位中定義的型別中，必須參考型別|
|[編譯器警告 (層級 1) C4692](../../error-messages/compiler-warnings/compiler-warning-level-1-c4692.md)|'function': 非私用成員的簽章含有組件私用原生類型 'native_type'|
|[編譯器警告 （層級 1，錯誤） C4693](../../error-messages/compiler-warnings/compiler-warning-c4693.md)|'class': 密封抽象類別不能有任何執行個體成員 '執行個體成員'|
|[編譯器警告 （層級 1，錯誤） C4694](../../error-messages/compiler-warnings/compiler-warning-c4694.md)|'class': 密封抽象類別不能有基底類別 'base_class'|
|編譯器警告 （層級 1） C4695|#pragma execution_character_set: '字元集' 不是支援的引數： 目前只支援 'utf-8' 支援|
|編譯器警告 （層級 1） C4696|/ 超出範圍; ZBvalue1 選項假設 'value2'|
|[編譯器警告 (層級 1 和層級 4) C4700](../../error-messages/compiler-warnings/compiler-warning-level-1-and-level-4-c4700.md)|未初始化的區域變數 'name' 使用|
|[編譯器警告 (層級 4) C4701](../../error-messages/compiler-warnings/compiler-warning-level-4-c4701.md)|可能未初始化的區域變數 'name' 使用|
|[編譯器警告 (層級 4) C4702](../../error-messages/compiler-warnings/compiler-warning-level-4-c4702.md)|無法連線到的程式碼|
|[編譯器警告 (層級 4) C4703](../../error-messages/compiler-warnings/compiler-warning-level-4-c4703.md)|可能未初始化的本機指標變數 '%s' 使用|
|[編譯器警告 (層級 4) C4706](../../error-messages/compiler-warnings/compiler-warning-level-4-c4706.md)|條件運算式中使用指派運算子|
|[編譯器警告 (層級 4) C4709](../../error-messages/compiler-warnings/compiler-warning-level-4-c4709.md)|陣列索引運算式中的逗號運算子|
|[編譯器警告 (層級 4) C4710](../../error-messages/compiler-warnings/compiler-warning-level-4-c4710.md)|'function': 未內嵌函式|
|[編譯器警告 (層級 1) C4711](../../error-messages/compiler-warnings/compiler-warning-level-1-c4711.md)|函式 'function' 被自動內嵌展開|
|[編譯器警告 (層級 4) C4714](../../error-messages/compiler-warnings/compiler-warning-level-4-c4714.md)|函式 'function' 標記為 __forceinline 無法內嵌|
|[編譯器警告 (層級 1) C4715](../../error-messages/compiler-warnings/compiler-warning-level-1-c4715.md)|'function': 不是所有控制路徑都傳回值|
|[編譯器警告 （層級 1，錯誤） C4716](../../error-messages/compiler-warnings/compiler-warning-level-1-c4716.md)|'function': 必須傳回值|
|[編譯器警告 (層級 1) C4717](../../error-messages/compiler-warnings/compiler-warning-level-1-c4717.md)|'function': 在所有控制路徑上的遞迴，函式會導致執行階段堆疊溢位|
|[編譯器警告 （層級 4） C4718](compiler-warning-level-4-c4718.md)|'function call': 遞迴呼叫沒有任何副作用，刪除|
|編譯器警告 （層級 1） C4719|找到指定 Qfast 時-使用 'f' 做為尾碼表示單精確度的雙精度浮點常數|
|編譯器警告 （層級 2） C4720|內嵌組合語言報告: 'message'|
|編譯器警告 （層級 1） C4721|'function': 無法當做內建函式|
|[編譯器警告 （層級 1） C4722](compiler-warning-level-1-c4722.md)|'function': 解構函式從未返回，可能有記憶體遺漏|
|[編譯器警告 (層級 3) C4723](../../error-messages/compiler-warnings/compiler-warning-level-3-c4723.md)|可能除以 0|
|[編譯器警告 （層級 3） C4724](compiler-warning-level-3-c4724.md)|MOD 的模數可能為 0|
|編譯器警告 （層級 3） C4725|指令在一些 Pentium 上可能不正確|
|[編譯器警告 (層級 1) C4727](../../error-messages/compiler-warnings/compiler-warning-level-1-c4727.md)|Obj_file_1 和 obj_file_2 中找到的相同時間戳記的 PCH 具名 pch_file。  使用第一個 PCH。|
|編譯器警告 （層級 1） C4728|/Yl-選項忽略，因為 PCH 參考是必要項|
|編譯器警告 （層級 4） C4729|依據 flow graph 產生的警告，發現函式太大|
|[編譯器警告 (層級 1) C4730](../../error-messages/compiler-warnings/compiler-warning-level-1-c4730.md)編譯器警告 （層級 1） C4730|'main': 混合 _m64 和浮點運算式可能會導致不正確的程式碼|
|[編譯器警告 (層級 1) C4731](../../error-messages/compiler-warnings/compiler-warning-level-1-c4731.md)|'pointer': 框架指標暫存器的 「 註冊 」 修改內嵌組譯碼|
|編譯器警告 （層級 1） C4732|在此架構不支援內建函式 '%s'|
|[編譯器警告 (層級 1) C4733](../../error-messages/compiler-warnings/compiler-warning-level-1-c4733.md)|內嵌 asm 指定給 'FS:0': 未註冊為安全的處理常式的處理常式|
|[編譯器警告 (層級 3) C4738](../../error-messages/compiler-warnings/compiler-warning-level-3-c4738.md)|在記憶體中儲存 32 位元浮點結果，可能會損失效能|
|[編譯器警告 （層級 1） C4739](compiler-warning-level-1-c4739.md)|變數 'var' 的參考超過了它的儲存空間|
|[編譯器警告 (層級 4) C4740](../../error-messages/compiler-warnings/compiler-warning-level-4-c4740.md)|流量流入或流出內嵌組譯程式碼會隱藏全域最佳化|
|[編譯器警告 (層級 1) C4742](../../error-messages/compiler-warnings/compiler-warning-level-1-c4742.md)|'var' 有 'file1' 和 'file2' 中有不同的對齊： 和號碼|
|[編譯器警告 (層級 1) C4743](../../error-messages/compiler-warnings/compiler-warning-level-1-c4743.md)|'type' 具有 'file1' 和 'file2' 的不同大小： 數字和位元組數|
|[編譯器警告 (層級 1) C4744](../../error-messages/compiler-warnings/compiler-warning-level-1-c4744.md)|'var' 具有 'file1' 和 'file2' 中的不同類型: 'type1' 和 'type2'|
|[編譯器警告 C4746](../../error-messages/compiler-warnings/compiler-warning-c4746.md)|暫時性存取的 '*運算式*' 受限於 /volatile:\<iso&#124;ms > 設定; 請考慮使用 __iso_volatile_load/store 內建函式|
|[編譯器警告 (層級 1) C4747](../../error-messages/compiler-warnings/compiler-warning-level-1-c4747.md)|呼叫受控 ' 進入點 ':Managed 程式碼可能不會執行載入器鎖定，包括 DLL 進入點和從 DLL 進入點到達的呼叫下|
|編譯器警告 （層級 4） C4749|有條件地支援： offsetof 套用至非標準配置類型 '*型別*'|
|[編譯器警告 （層級 1） C4750](compiler-warning-level-1-c4750.md)|'identifier': 函式中有 _alloca() 內嵌成迴圈|
|編譯器警告 （層級 4） C4751|/arch: avx 不適用於 intel （) Streaming SIMD Extensions 內嵌 ASM 中，|
|編譯器警告 （層級 4） C4752|找到 intel （) Advanced Vector Extensions;請考慮使用 /arch: avx|
|[編譯器警告 （層級 4） C4754](compiler-warning-level-4-c4754.md)|位於 %s(%d) 的比較中的算術運算的轉換規則表示的一個分支無法執行。 轉換 '%s' '%s' （或 %d 位元組的類似類型）。|
|編譯器警告 C4755|位於 %s(%d) 的比較中的算術運算的轉換規則表示的一個分支無法執行中的內嵌函式。 轉換 '%s' '%s' （或 %d 位元組的類似類型）。|
|[編譯器警告 (層級 2) C4756](../../error-messages/compiler-warnings/compiler-warning-level-2-c4756.md)|在常數算術中溢位|
|編譯器警告 （層級 4） C4757|註標是大型 unsigned 的值，您要使用負的常數？|
|[編譯器警告 （層級 4） C4764](compiler-warning-level-4-c4764.md)|無法對齊超過 16 位元組的攔截物件|
|編譯器警告 （層級 4） C4767|區段名稱 '%s' 超過 8 個字元，將由連結器截斷|
|編譯器警告 （層級 3） C4768|會忽略連結規格前的 __declspec 屬性|
|編譯器警告 C4770|部分驗證的列舉 '*名稱*' 做為索引|
|編譯器警告 C4771|必須使用簡單指標建立界限已忽略 MPX 內建函式|
|[編譯器警告 （層級 1，錯誤） C4772](../../error-messages/compiler-warnings/compiler-warning-level-1-c4772.md)|#import 參考型別從遺漏的類型程式庫;' missing_type' 做為預留位置|
|編譯器警告 （層級 4） C4774|'*字串*': 格式字串引數中必須要有*數目*不是字串常值|
|編譯器警告 （層級 3） C4775|在格式字串中使用非標準擴充 '*字串*'的函式'*函式*'|
|編譯器警告 （層級 1） C4776|' %*字元*'中不允許函式的格式字串'*函式*'|
|編譯器警告 （層級 4） C4777|'*函式*': 格式字串'*字串*'需要類型的引數'*type1*'，但 variadic 引數*數目*具有類型 '*type2*'|
|編譯器警告 （層級 3） C4778|'*函式*': 未結束的格式字串'*字串*'|
|[編譯器警告 (層級 1) C4788](../../error-messages/compiler-warnings/compiler-warning-level-1-c4788.md)|'identifier': 識別項被截斷成 'number' 個字元|
|[編譯器警告 (層級 1) C4789](../../error-messages/compiler-warnings/compiler-warning-level-1-c4789.md)|大小 N 位元組的緩衝區 'identifier' 會溢位；將從位移 L 開始寫入 M 位元組|
|編譯器警告 （層級 2） C4792|函式 '%s' 使用 sysimport 宣告並從原生程式碼; 參考匯入程式庫需要連結|
|[編譯器警告 (層級 1 和 3) C4793](../../error-messages/compiler-warnings/compiler-warning-level-1-and-3-c4793.md)|'function': 函式編譯為原生： \n\t'reason'|
|[編譯器警告 （層級 1） C4794](compiler-warning-level-1-c4794.md)|執行緒區域儲存區變數 '%s' 從 '%s' 變更為 '%s' 的區段|
|[編譯器警告 (層級 1) C4799](../../error-messages/compiler-warnings/compiler-warning-level-1-c4799.md)|函式 'function' 有沒有 EMMS 指令|