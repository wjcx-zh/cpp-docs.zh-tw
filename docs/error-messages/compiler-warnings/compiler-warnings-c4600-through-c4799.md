---
title: "編譯器警告 C4600 到 C4799 |Microsoft 文件"
ms.date: 10/25/2017
ms.technology: cpp-tools
ms.topic: error-reference
f1_keywords:
- C4602
- C4603
- C4609
- C4612
- C4613
- C4620
- C4622
- C4629
- C4631
- C4634
- C4635
- C4636
- C4637
- C4638
- C4645
- C4646
- C4655
- C4657
- C4658
- C4662
- C4670
- C4671
- C4672
- C4674
- C4676
- C4678
- C4681
- C4682
- C4685
- C4688
- C4689
- C4690
- C4693
- C4694
- C4695
- C4696
- C4718
- C4719
- C4720
- C4721
- C4722
- C4724
- C4725
- C4728
- C4729
- C4732
- C4739
- C4750
- C4751
- C4752
- C4754
- C4755
- C4757
- C4764
- C4767
- C4770
- C4792
- C4794
dev_langs: C++
ms.assetid: 22bd4392-f3be-445c-9f23-6126aebac901
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 456d35247f25d20684e8b6957d61428a2b113ca0
ms.sourcegitcommit: 69632887f7a85f4841c49b4c1353d3144927a52c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/11/2017
---
# <a name="compiler-warnings-c4600-through-c4799"></a>編譯器警告 C4600 到 C4799

這一部分的文件中的文章包含 Visual c + + 編譯器警告的資訊子集。 您可以在此存取資訊或者，在 Visual Studio 中的 輸出 視窗中，您可以選取錯誤代碼，然後按下 F1 鍵。

> [!NOTE]
> 並非每個[!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)]錯誤或警告會記載於 MSDN 中。 在許多情況下，診斷訊息會提供所有可用的資訊。 如果您認為錯誤訊息需要補充說明，請告訴我們。 您可以使用這個頁面上的回函表單或移至 Visual Studio 中的功能表列並選擇**協助**，**回報 Bug**，或您可以提出建議或 bug 報告上[Microsoft Connect](http://connect.microsoft.com/VisualStudio).

您可能會發現其他協助的 MSDN 公共論壇上錯誤及警告。 [Visual c + + 語言](http://go.microsoft.com/fwlink/?LinkId=158195)論壇是關於問題及討論[!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)]語言語法和編譯器。 [Visual c + + 一般](http://go.microsoft.com/fwlink/?LinkId=158194)論壇是關於問題[!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)]其他論壇中沒有討論之。 您也可能會在找到關於錯誤和警告的說明[堆疊溢位](http://stackoverflow.com/)。

## <a name="in-this-section"></a>本章節內容

|警告|訊息|
|-------------|-------------|
|[編譯器警告 (層級 1) C4600](../../error-messages/compiler-warnings/compiler-warning-level-1-c4600.md)|#pragma '巨集名稱': 必須是有效的非空白字串|
|編譯器警告 （層級 1） C4602|#pragma pop_macro: '巨集名稱' #pragma push_macro，此識別項|
|編譯器警告 （層級 1） C4603|'*識別碼*': 巨集未定義或定義是不同，在使用先行編譯標頭之後|
|編譯器警告 （層級 1） C4604|'*類型*': 引數傳值方式傳遞原生和 managed 界限之間需要有效的複製建構函式。 否則執行階段行為未定義|
|編譯器警告 （層級 1） C4605|'/D*巨集*' 目前的命令列上指定，但未指定建置先行編譯標頭時|
|[編譯器警告 (層級 1) C4606](../../error-messages/compiler-warnings/compiler-warning-level-1-c4606.md)|#pragma 警告： 警告編號' 忽略;程式碼分析警告不會支援警告層級產生關聯|
|[編譯器警告 (層級 3) C4608](../../error-messages/compiler-warnings/compiler-warning-level-3-c4608.md)|'union_member' 已由初始設定式清單中的等位成員 'union_member' 初始化|
|編譯器警告 （層級 3，錯誤） C4609|'*type1*'衍生自預設介面'*介面*'type' 上*type2*'。 使用不同的預設介面 '*type1*'，或中斷基底/衍生關聯性。|
|[編譯器警告 (層級 4) C4610](../../error-messages/compiler-warnings/compiler-warning-level-4-c4610.md)|'class' 物件無法執行個體化-使用者定義的建構函式所需|
|[編譯器警告 (層級 4) C4611](../../error-messages/compiler-warnings/compiler-warning-level-4-c4611.md)|'function' 和 c + + 物件解構間的互動是不可移植|
|編譯器警告 （層級 1） C4612|Include 檔檔名錯誤|
|編譯器警告 （層級 1） C4613|'*符號*': 無法變更區段類別|
|[編譯器警告 (層級 1) C4615](../../error-messages/compiler-warnings/compiler-warning-level-1-c4615.md)|#pragma 警告： 未知的使用者警告類型|
|[編譯器警告 (層級 1) C4616](../../error-messages/compiler-warnings/compiler-warning-level-1-c4616.md)|#pragma 警告： 警告編號 'number' 不是有效的編譯器警告|
|[編譯器警告 (層級 1) C4618](../../error-messages/compiler-warnings/compiler-warning-level-1-c4618.md)|pragma 參數包含空白的字串。已忽略 pragma|
|[編譯器警告 (層級 3) C4619](../../error-messages/compiler-warnings/compiler-warning-level-3-c4619.md)|#pragma warning: 沒有警告編號 'number'|
|編譯器警告 （層級 1） C4620|找不到類型 'type' 後置格式的 'operator ++'，已改用前置格式|
|[編譯器警告 (層級 1) C4621](../../error-messages/compiler-warnings/compiler-warning-level-1-c4621.md)|沒有運算子後置格式 '-' 找到類型 'type'，改用前置格式|
|編譯器警告 （層級 3） C4622|覆寫偵錯資訊建立期間形成的目的檔中先行編譯標頭: 'file'|
|[編譯器警告 (層級 4) C4623](../../error-messages/compiler-warnings/compiler-warning-level-4-c4623.md)|'derived class': 預設建構函式已隱含定義為刪除，因為基底類別預設建構函式無法存取或已刪除|
|[編譯器警告 (層級 1) C4624](../../error-messages/compiler-warnings/compiler-warning-level-1-c4624.md)|'derived class': 解構函式已隱含定義為刪除，因為基底類別解構函式無法存取或已刪除|
|[編譯器警告 (層級 4) C4625](../../error-messages/compiler-warnings/compiler-warning-level-4-c4625.md)|'derived class': 複製建構函式已隱含定義為刪除，因為基底類別複製建構函式無法存取或已刪除|
|[編譯器警告 (層級 4) C4626](../../error-messages/compiler-warnings/compiler-warning-level-4-c4626.md)|'derived class': 指派運算子已隱含定義為刪除，因為基底類別指派運算子是無法存取或已刪除|
|[編譯器警告 (層級 1) C4627](../../error-messages/compiler-warnings/compiler-warning-level-1-c4627.md)|'\<識別項 >': 尋找先行編譯標頭使用時略過|
|[編譯器警告 (層級 1) C4628](../../error-messages/compiler-warnings/compiler-warning-level-1-c4628.md)|不支援使用 -Ze 的雙拼詞。 字元順序 'digraph' 沒有解譯為 '%s' 的替代 token|
|編譯器警告 （層級 4） C4629|使用了雙拼詞，字元順序 'digraph' 被解譯為語彙基元 'char' (如果這不是您想要的，請在兩個字元之間插入一個空格)|
|[編譯器警告 (層級 1) C4630](../../error-messages/compiler-warnings/compiler-warning-level-1-c4630.md)|'symbol': 'extern' 儲存類別規範不合法成員定義上|
|編譯器警告 （層級 2） C4631|MSXML 或 XPath 無法使用，將不會處理 XML 文件註解。 原因|
|[編譯器警告 (層級 1) C4632](../../error-messages/compiler-warnings/compiler-warning-level-1-c4632.md)|XML 文件註解： 檔案-存取遭拒： 原因|
|[編譯器警告 (層級 3) C4633](../../error-messages/compiler-warnings/compiler-warning-level-3-c4633.md)|XML 文件註解目標： 錯誤： 原因|
|編譯器警告 （層級 4） C4634|XML 文件註解目標： 無法套用： 原因|
|編譯器警告 （層級 3） C4635|XML 文件註解目標: XML 格式錯誤: 原因|
|編譯器警告 （層級 3） C4636|套用至建構的 XML 文件註解： 標記必須是非空白 'attribute' 屬性。|
|編譯器警告 （層級 3 和層級 4） C4637|XML 文件註解目標：\<包括 > 標記已捨棄。 原因|
|編譯器警告 （層級 3） C4638|XML 文件註解目標： 未知符號 'symbol' 參考。|
|[編譯器警告 (層級 4) C4639](../../error-messages/compiler-warnings/compiler-warning-level-4-c4639.md)|MSXML 錯誤，將不會處理註解的 XML 文件。 原因|
|[編譯器警告 (層級 3) C4640](../../error-messages/compiler-warnings/compiler-warning-level-3-c4640.md)|'instance': 區域靜態物件的建構不是安全執行緒|
|[編譯器警告 (層級 3) C4641](../../error-messages/compiler-warnings/compiler-warning-level-3-c4641.md)|XML 文件註解有模稜兩可的交互參考：|
|編譯器警告 （層級 3） C4645|使用 __declspec(noreturn) 宣告的函式有傳回的陳述式|
|編譯器警告 （層級 3） C4646|使用 __declspec(noreturn) 宣告的函式有非 void 的傳回類型|
|編譯器警告 （層級 3） C4647|行為變更： __is_pod (*類型*) 在舊版中有不同的值|
|編譯器警告 （層級 3） C4648|忽略標準的屬性 '未以 carries_dependency'|
|編譯器警告 （層級 3） C4649|在此內容中就會忽略屬性|
|[編譯器警告 (層級 1) C4650](../../error-messages/compiler-warnings/compiler-warning-level-1-c4650.md)|先行編譯標頭; 不在偵錯資訊只有全域符號標頭中的可使用|
|[編譯器警告 (層級 1) C4651](../../error-messages/compiler-warnings/compiler-warning-level-1-c4651.md)|指定先行編譯標頭，但不適用於目前的編譯 ' 定義 '|
|[編譯器警告 (層級 1) C4652](../../error-messages/compiler-warnings/compiler-warning-level-1-c4652.md)|編譯器選項 'option' 與先行編譯標頭; 不一致目前的命令列選項會覆寫先行編譯標頭中定義|
|[編譯器警告 (層級 2) C4653](../../error-messages/compiler-warnings/compiler-warning-level-2-c4653.md)|編譯器選項 'option' 與先行編譯標頭; 不一致忽略目前的命令列選項|
|編譯器警告 （層級 4） C4654|先行編譯標頭包含放在之前的程式碼行都會被忽略。 程式碼加入先行編譯標頭。|
|編譯器警告 （層級 1） C4655|'symbol': 變數的類型是最新組建之後，新或其他處有不同定義|
|[編譯器警告 (層級 1) C4656](../../error-messages/compiler-warnings/compiler-warning-level-1-c4656.md)|'symbol': 資料類型的新或變更過的最新的組建，或其他處有不同定義|
|編譯器警告 （層級 1） C4657|運算式包含自上次組建之後才新增的資料類型|
|編譯器警告 （層級 1） C4658|'function': 函式原型自有新的最新的組建，或其他處有不同的宣告|
|[編譯器警告 (層級 1) C4659](../../error-messages/compiler-warnings/compiler-warning-level-1-c4659.md)|#pragma 'pragma': 使用保留的區段 'segment' 有未定義的行為，請使用 #pragma 註解 (linker，...)|
|[編譯器警告 (層級 1) C4661](../../error-messages/compiler-warnings/compiler-warning-level-1-c4661.md)|'identifier': 未提供明確樣板具現化要求的合適定義|
|編譯器警告 （層級 1） C4662|明確具現化 (Explicit Instantiation)；樣板類別 'identifier1' 沒有特製化 'identifier2' 用的定義|
|[編譯器警告 (層級 1) C4667](../../error-messages/compiler-warnings/compiler-warning-level-1-c4667.md)|'function': 沒有函式樣板定義符合強制具現化|
|[編譯器警告 (層級 4) C4668](../../error-messages/compiler-warnings/compiler-warning-level-4-c4668.md)|'symbol' 未定義成前置處理器巨集，以 '0' 取代 'directive'|
|[編譯器警告 (層級 1) C4669](../../error-messages/compiler-warnings/compiler-warning-level-1-c4669.md)|'cast': 不安全的轉換: 'class' 是 managed 型別物件|
|編譯器警告 （層級 4） C4670|'identifier': 此基底類別是無法存取|
|編譯器警告 （層級 4） C4671|'identifier': 複製建構函式是無法存取|
|編譯器警告 （層級 4） C4672|'identifier1': 模稜兩可。 第一個看到的當做 'identifier2'|
|[編譯器警告 (層級 4) C4673](../../error-messages/compiler-warnings/compiler-warning-level-4-c4673.md)|下列類型時擲回 'identifier' 不會考慮使用時，catch|
|編譯器警告 （層級 1） C4674|'method' 必須宣告為 'static'，而且只能有一個參數|
|編譯器警告 （層級 4） C4676|'%s': 解構函式是無法存取|
|[編譯器警告 (層級 1) C4677](../../error-messages/compiler-warnings/compiler-warning-level-1-c4677.md)|'function': 非私用成員簽章含有組件私用類型 'private_type'|
|編譯器警告 （層級 1） C4678|基底類別 'base_type' 比 'derived_type' 更難以存取|
|[編譯器警告 (層級 1) C4679](../../error-messages/compiler-warnings/compiler-warning-level-1-c4679.md)|'member': 無法匯入成員|
|[編譯器警告 (層級 4) C4680](../../error-messages/compiler-warnings/compiler-warning-level-4-c4680.md)|'class': coclass 不指定的預設介面。|
|編譯器警告 （層級 4） C4681|'class': coclass 不指定為事件來源的預設介面|
|編譯器警告 （層級 4） C4682|'parameter': 沒有方向參數屬性指定，預設為 [in]|
|[編譯器警告 (層級 1) C4683](../../error-messages/compiler-warnings/compiler-warning-level-1-c4683.md)|'function': 事件來源有 'out' 的參數。當攔截多個事件處理常式時務必謹慎|
|[編譯器警告 (層級 1) C4684](../../error-messages/compiler-warnings/compiler-warning-level-1-c4684.md)|'attribute': 警告!! 屬性可能造成無效的程式碼產生： 請謹慎使用|
|編譯器警告 （層級 1） C4685|剖析樣板參數時需要 '> >'，但卻找到 '>>'|
|[編譯器警告 (層級 3) C4686](../../error-messages/compiler-warnings/compiler-warning-level-3-c4686.md)|'user-defined type': 行為可能有變更，在 UDT 傳回呼叫慣例中發生變更|
|[編譯器警告 （錯誤） C4687](../../error-messages/compiler-warnings/compiler-warning-c4687.md)|'class': 密封抽象類別不能實作介面 'interface'|
|編譯器警告 （層級 1） C4688|'constraint': 條件約束清單含有組件私用類型 'type'，將無法由組件外部存取|
|編譯器警告 （層級 1） C4689|'%c'： 不支援 #pragma detect_mismatch; 中的字元忽略 #pragma|
|編譯器警告 （層級 4） C4690|[emitidl (pop)]: pop|
|[編譯器警告 (層級 1) C4691](../../error-messages/compiler-warnings/compiler-warning-level-1-c4691.md)|'type': 未參考組件 'file'，而是會使用目前的轉譯單位中定義的型別中，必須有參考類型|
|[編譯器警告 (層級 1) C4692](../../error-messages/compiler-warnings/compiler-warning-level-1-c4692.md)|'function': 非私用成員的簽章含有組件私用原生類型 'native_type'|
|[編譯器警告 （層級 1，錯誤） C4693](../../error-messages/compiler-warnings/compiler-warning-c4693.md)|'class': 密封抽象類別不能有任何執行個體成員 '執行個體 member'|
|[編譯器警告 （層級 1，錯誤） C4694](../../error-messages/compiler-warnings/compiler-warning-c4694.md)|'class': 密封抽象類別不能有基底類別 'base_class'|
|編譯器警告 （層級 1） C4695|#pragma execution_character_set: '字元集' 不是支援的引數： 目前只支援 'utf-8' 支援|
|編譯器警告 （層級 1） C4696|/ ZBvalue1 選項超出範圍。假設 'value2'|
|[編譯器警告 (層級 1 和層級 4) C4700](../../error-messages/compiler-warnings/compiler-warning-level-1-and-level-4-c4700.md)|未初始化的區域變數 'name' 使用|
|[編譯器警告 (層級 4) C4701](../../error-messages/compiler-warnings/compiler-warning-level-4-c4701.md)|可能未初始化的區域變數 'name' 使用|
|[編譯器警告 (層級 4) C4702](../../error-messages/compiler-warnings/compiler-warning-level-4-c4702.md)|無法連線到程式碼|
|[編譯器警告 (層級 4) C4703](../../error-messages/compiler-warnings/compiler-warning-level-4-c4703.md)|可能未初始化的本機指標變數 '%s' 使用|
|[編譯器警告 (層級 4) C4706](../../error-messages/compiler-warnings/compiler-warning-level-4-c4706.md)|條件運算式中使用指派運算子|
|[編譯器警告 (層級 4) C4709](../../error-messages/compiler-warnings/compiler-warning-level-4-c4709.md)|陣列索引運算式中的逗號運算子|
|[編譯器警告 (層級 4) C4710](../../error-messages/compiler-warnings/compiler-warning-level-4-c4710.md)|'function': 未內嵌函式|
|[編譯器警告 (層級 1) C4711](../../error-messages/compiler-warnings/compiler-warning-level-1-c4711.md)|函式 'function' 被自動內嵌展開|
|[編譯器警告 (層級 4) C4714](../../error-messages/compiler-warnings/compiler-warning-level-4-c4714.md)|函式 'function' 標記為 __forceinline 無法內嵌|
|[編譯器警告 (層級 1) C4715](../../error-messages/compiler-warnings/compiler-warning-level-1-c4715.md)|'function': 不是所有控制路徑都傳回值|
|[編譯器警告 （層級 1，錯誤） C4716](../../error-messages/compiler-warnings/compiler-warning-level-1-c4716.md)|'function': 必須傳回值|
|[編譯器警告 (層級 1) C4717](../../error-messages/compiler-warnings/compiler-warning-level-1-c4717.md)|'function': 在所有控制路徑上的遞迴，函式會導致執行階段堆疊溢位|
|編譯器警告 （層級 4） C4718|'function call': 遞迴呼叫沒有任何副作用，刪除|
|編譯器警告 （層級 1） C4719|指定 Qfast-使用 'f' 當做字尾以單精確度時，找到雙精度浮點常數|
|編譯器警告 （層級 2） C4720|內嵌組合語言報告: 'message'|
|編譯器警告 （層級 1） C4721|'function': 無法當做內建|
|編譯器警告 （層級 1） C4722|'function': 解構函式從未返回，可能發生記憶體流失的問題|
|[編譯器警告 (層級 3) C4723](../../error-messages/compiler-warnings/compiler-warning-level-3-c4723.md)|可能除以 0|
|編譯器警告 （層級 3） C4724|MOD 的模數可能為 0|
|編譯器警告 （層級 3） C4725|指令在一些 Pentium 上可能不正確|
|[編譯器警告 (層級 1) C4727](../../error-messages/compiler-warnings/compiler-warning-level-1-c4727.md)|Obj_file_1 和 obj_file_2 中找到相同的時間戳記的 PCH 具名 pch_file。  使用第一個 PCH。|
|編譯器警告 （層級 1） C4728|/Yl-選項忽略，因為 PCH 參考是必要|
|編譯器警告 （層級 4） C4729|依據 flow graph 產生的警告，發現函式太大|
|[編譯器警告 (層級 1) C4730](../../error-messages/compiler-warnings/compiler-warning-level-1-c4730.md)編譯器警告 （層級 1） C4730|'main': 混合 _m64 和浮點運算式可能會導致不正確的程式碼|
|[編譯器警告 (層級 1) C4731](../../error-messages/compiler-warnings/compiler-warning-level-1-c4731.md)|'pointer': 框架指標暫存器 'register' 修改內嵌組譯碼|
|編譯器警告 （層級 1） C4732|在這種架構不支援內建函式 '%s'|
|[編譯器警告 (層級 1) C4733](../../error-messages/compiler-warnings/compiler-warning-level-1-c4733.md)|內嵌 asm 指定給 'Fs: 0': 未註冊為安全的處理常式的處理常式|
|[編譯器警告 (層級 3) C4738](../../error-messages/compiler-warnings/compiler-warning-level-3-c4738.md)|在記憶體中儲存 32 位元浮點結果，可能會損失效能|
|編譯器警告 （層級 1） C4739|變數 'var' 的參考超過了它的儲存空間|
|[編譯器警告 (層級 4) C4740](../../error-messages/compiler-warnings/compiler-warning-level-4-c4740.md)|進出內嵌組譯程式碼的流程會隱藏全域最佳化|
|[編譯器警告 (層級 1) C4742](../../error-messages/compiler-warnings/compiler-warning-level-1-c4742.md)|'var' 有 'file1' 和 'file2' 在不同的對齊： 和號碼|
|[編譯器警告 (層級 1) C4743](../../error-messages/compiler-warnings/compiler-warning-level-1-c4743.md)|'type' 具有 'file1' 和 'file2' 的不同大小： 數字和位元組數|
|[編譯器警告 (層級 1) C4744](../../error-messages/compiler-warnings/compiler-warning-level-1-c4744.md)|'var' 具有 'file1' 和 'file2' 中的不同類型: 'type1' 和 'type2'|
|[編譯器警告 C4746](../../error-messages/compiler-warnings/compiler-warning-c4746.md)|暫時性存取 '*運算式*' 受限於 /volatile:\<iso &#124; ms > 設定; 請考慮使用 __iso_volatile_load/store 內建函式|
|[編譯器警告 (層級 1) C4747](../../error-messages/compiler-warnings/compiler-warning-level-1-c4747.md)|呼叫 managed '進入點': Managed 程式碼不會執行載入器鎖定，包括 DLL 進入點和從 DLL 進入點到達的呼叫下|
|編譯器警告 （層級 4） C4749|有條件地支援： 套用至 non standard 配置類型的 offsetof '*類型*'|
|編譯器警告 （層級 1） C4750|'identifier': 函式中有 _alloca() 內嵌成迴圈|
|編譯器警告 （層級 4） C4751|/arch: avx 不適用於 intel （) Streaming SIMD Extensions，內嵌 ASM 中|
|編譯器警告 （層級 4） C4752|找到 intel （) Advanced Vector Extensions;請考慮使用 /arch: avx|
|編譯器警告 （層級 4） C4754|位於比較中有算術運算的轉換規則表示該一個分支無法執行。 轉換 '%s' '%s' （或 %d 位元組的類似類型）。|
|編譯器警告 C4755|位於比較中有算術運算的轉換規則表示一個分支無法執行中的內嵌函式。 轉換 '%s' '%s' （或 %d 位元組的類似類型）。|
|[編譯器警告 (層級 2) C4756](../../error-messages/compiler-warnings/compiler-warning-level-2-c4756.md)|在常數算術中溢位|
|編譯器警告 （層級 4） C4757|註標是大型 unsigned 的值，您要使用負的常數？|
|編譯器警告 （層級 4） C4764|無法對齊超過 16 位元組的攔截物件|
|編譯器警告 （層級 4） C4767|區段名稱 '%s' 超過 8 個字元，將由連結器截斷|
|編譯器警告 （層級 3） C4768|就會忽略 __declspec 屬性之前連結規格|
|編譯器警告 C4770|部分驗證的列舉 '*名稱*' 做為索引|
|編譯器警告 C4771|您必須使用簡單的指標; 建立界限忽略 MPX 內建函式|
|[編譯器警告 （層級 1，錯誤） C4772](../../error-messages/compiler-warnings/compiler-warning-level-1-c4772.md)|#import 參考型別從遺漏的類型程式庫。' missing_type' 做為預留位置|
|編譯器警告 （層級 4） C4774|'*字串*': 格式字串引數中必須要有*數目*不是字串常值|
|編譯器警告 （層級 3） C4775|在格式字串中使用非標準擴充 '*字串*'的函式'*函式*'|
|編譯器警告 （層級 1） C4776|' %*字元*'中不允許函式的格式字串'*函式*'|
|編譯器警告 （層級 4） C4777|'*函式*': 格式字串'*字串*'需要類型的引數'*type1*'，但 variadic 引數*數目*具有類型 '*type2*'|
|編譯器警告 （層級 3） C4778|'*函式*': 有未結束的格式字串'*字串*'|
|[編譯器警告 (層級 1) C4788](../../error-messages/compiler-warnings/compiler-warning-level-1-c4788.md)|'identifier': 識別項被截斷成 'number' 個字元|
|[編譯器警告 (層級 1) C4789](../../error-messages/compiler-warnings/compiler-warning-level-1-c4789.md)|大小 N 位元組的緩衝區 'identifier' 會溢位；將從位移 L 開始寫入 M 位元組|
|編譯器警告 （層級 2） C4792|使用 sysimport 宣告並從原生程式碼; 參考的函式 '%s'匯入程式庫需要連結|
|[編譯器警告 (層級 1 和 3) C4793](../../error-messages/compiler-warnings/compiler-warning-level-1-and-3-c4793.md)|'function': 函式編譯為原生： \n\t'reason'|
|編譯器警告 （層級 1） C4794|執行緒區域儲存區變數 '%s' 從 '%s' 變更為 '%s' 上的線段|
|[編譯器警告 (層級 1) C4799](../../error-messages/compiler-warnings/compiler-warning-level-1-c4799.md)|函式 'function' 有沒有 EMMS 指令|