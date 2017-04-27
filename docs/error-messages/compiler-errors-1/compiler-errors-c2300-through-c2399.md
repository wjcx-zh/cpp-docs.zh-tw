---
title: "編譯器錯誤 s C2300 Through C2399 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2303
- C2304
- C2305
- C2306
- C2314
- C2321
- C2323
- C2328
- C2329
- C2330
- C2331
- C2335
- C2336
- C2339
- C2340
- C2342
- C2343
- C2347
- C2354
- C2358
- C2359
- C2363
- C2366
- C2367
- C2398
- C2399
helpviewer_keywords:
- C2303
- C2304
- C2305
- C2306
- C2314
- C2321
- C2323
- C2328
- C2329
- C2330
- C2331
- C2335
- C2336
- C2339
- C2340
- C2342
- C2343
- C2347
- C2354
- C2358
- C2359
- C2363
- C2366
- C2367
- C2398
- C2399
dev_langs:
- C++
ms.assetid: 07ca45b5-b2f0-4049-837b-40a7a3caed88
caps.latest.revision: 14
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 4bac7b2942f9d72674b8092dc7bf64174dd3c349
ms.openlocfilehash: 8d8925a68ffbb7ba607e37be8db5eca33300ef23
ms.lasthandoff: 04/24/2017

---
# <a name="compiler-errors-c2300-through-c2399"></a>編譯器錯誤s C2300 Through C2399
這部分文件中的文章包含 Visual C++ 編譯器錯誤的子區段的相關資訊。 您可以在此存取資訊，或是在 Visual Studio 的 [ **輸出** ] 視窗，您可以選取錯誤代碼然後選擇 F1 鍵。  
  
> [!NOTE]
>  並非每個[!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)]錯誤會記載於 MSDN 中。 在許多情況下，診斷訊息會提供所有可用的資訊。 如果您認為錯誤訊息需要補充說明，請告訴我們。 您可以使用這個頁面上的回函表單或移至 Visual Studio 中的功能表列並選擇**協助**，**回報 Bug**，或您可以提出建議或 bug 報告上[Microsoft Connect](http://connect.microsoft.com/VisualStudio)。  
  
 您可能會發現其他協助的 MSDN 公共論壇上錯誤及警告。 [Visual c + + 語言](http://go.microsoft.com/fwlink/?LinkId=158195)論壇是關於問題及討論[!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)]語言語法和編譯器。 [Visual c + + 一般](http://go.microsoft.com/fwlink/?LinkId=158194)論壇是關於問題[!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)]其他論壇中沒有討論之。 您也可能會在找到關於錯誤和警告的說明[堆疊溢位](http://stackoverflow.com/)。  
  
|錯誤|訊息|  
|-----------|-------------|  
|[編譯器錯誤 C2300](compiler-error-c2300.md)|'*類別*': 類別沒有呼叫解構函式' ~*類別*'|  
|[編譯器錯誤 C2301](compiler-error-c2301.md)|左邊的 '-> ~*識別碼*' 必須指向類別/結構/等位|  
|[編譯器錯誤 C2302](compiler-error-c2302.md)|左邊 '。 ~*識別碼*' 必須有類別/結構/等位型別|  
|編譯器錯誤 C2303|協同程式中，無法使用結構化例外狀況處理|  
|編譯器錯誤 C2304|'*關鍵字*' 不能在 catch 區塊|  
|編譯器錯誤 C2305|'*檔案*' 不包含此模組的偵錯資訊|  
|編譯器錯誤 C2306|'*檔案*' 不包含此模組最新的偵錯資訊|  
|[編譯器錯誤 C2307](compiler-error-c2307.md)|pragma*指示詞*必須移動函式以外中，如果已啟用累加編譯|  
|[編譯器錯誤 C2308](compiler-error-c2308.md)|指定要結合的字串彼此不相符，無法執行|  
|[編譯器錯誤 C2309](compiler-error-c2309.md)|catch 處理常式必須使用括號括住例外狀況的宣告|  
|[編譯器錯誤 C2310](compiler-error-c2310.md)|catch 處理常式必須指定一個類型|  
|[編譯器錯誤 C2311](compiler-error-c2311.md)|'*類型*': 被 '...' 攔截 在行*數目*|  
|[編譯器錯誤 C2312](compiler-error-c2312.md)|'*type1*': 被攔截'*type2*' 在行*數目*|  
|[編譯器錯誤 C2313](compiler-error-c2313.md)|'*type1*': 被參考 ('*type2*') 的一行*數目*|  
|編譯器錯誤 C2314|關鍵字 '*keyword1*' 已被取代︰ 使用 '*keyword2*' 改為|  
|[編譯器錯誤 C2315](compiler-error-c2315.md)|'*type1*': 參考被攔截'*type2*' 在行*數目*|  
|[編譯器錯誤 C2316](compiler-error-c2316.md)|'*類型*': 無法攔截，因為解構函式及/或複製建構函式無法存取或已刪除|  
|[編譯器錯誤 C2317](compiler-error-c2317.md)|'try' 區塊開始於行 '*數目*' 沒有 catch 處理常式|  
|[編譯器錯誤 C2318](compiler-error-c2318.md)|沒有和 catch 處理常式關聯的 try 區塊|  
|[編譯器錯誤 C2319](compiler-error-c2319.md)|'try/catch' 之後必須是複合陳述式。 遺漏 '{'|  
|[編譯器錯誤 C2320](compiler-error-c2320.md)|必須是 ':' 遵循存取規範 '*規範*'|  
|編譯器錯誤 C2321|'*識別碼*' 是關鍵字，也不能在此內容中|  
|[編譯器錯誤 C2322](compiler-error-c2322.md)|'*識別碼*': dllimport 的位址'*識別碼*' 不是靜態的|  
|編譯器錯誤 C2323|'*識別碼*': 非成員運算子 new 或 delete 函式不可宣告為靜態，或在全域命名空間以外的命名空間|  
|[編譯器錯誤 C2324](compiler-error-c2324.md)|'*識別碼*': 非預期的右邊 ':: ~'|  
|[編譯器錯誤 C2325](compiler-error-c2325.md)|'*type1*': 未預期的類型，右邊的'-> ~': 必須是 '*type2*'|  
|[編譯器錯誤 C2326](compiler-error-c2326.md)|'*宣告子*': 函式無法存取'*識別碼*'|  
|[編譯器錯誤 C2327](compiler-error-c2327.md)|'*識別碼*': 不是型別名稱、 靜態或列舉值|  
|編譯器錯誤 C2328|'*關鍵字*': 不支援關鍵字|  
|編譯器錯誤 C2329|'*識別碼*': 沒有可用的函式的指標 __ptr64|  
|編譯器錯誤 C2330|'implementation_key( )' 只在由 #pragma start_map_region/stop_map_region 界限的區域中有效|  
|編譯器錯誤 C2331|若要存取 '*識別碼*'現在已經定義為'*accessibility1*'、 先前定義為'*accessibility2*'|  
|[編譯器錯誤 C2332](compiler-error-c2332.md)|'*typedef*': 遺漏標記名稱|  
|[編譯器錯誤 C2333](compiler-error-c2333.md)|'*函式*': 函式宣告中的錯誤; 略過函式主體|  
|[編譯器錯誤 C2334](compiler-error-c2334.md)|未預期的語彙基元，上述 '*語彙基元*'; 略過函式主體|  
|編譯器錯誤 C2335|'*識別碼*': 型別不能引入函式參數清單|  
|編譯器錯誤 C2336|'*類型*': 不合法的類型|  
|[編譯器錯誤 C2337](compiler-error-c2337.md)|'*屬性*': 找不到屬性|  
|[編譯器錯誤 C2338](compiler-error-c2338.md)|*（從外部提供者的錯誤訊息）*|  
|編譯器錯誤 C2339|'*識別碼*': 內嵌 IDL 中不合法的類型|  
|編譯器錯誤 C2340|'*識別碼*': 'static' 只可用在類別定義中|  
|[編譯器錯誤 C2341](compiler-error-c2341.md)|'*區段*': 您必須使用 #pragma data_seg、 code_seg 或前一個區段用於定義區段|  
|編譯器錯誤 C2342|語法錯誤: 衝突的類型限定詞|  
|編譯器錯誤 C2343|'*區段*': 衝突的區段屬性|  
|[編譯器錯誤 C2344](compiler-error-c2344.md)|對齊 (*數目*): 對齊必須是 2 的乘冪|  
|[編譯器錯誤 C2345](compiler-error-c2345.md)|對齊 (*數目*): 不合法的 align 值|  
|[編譯器錯誤 C2346](compiler-error-c2346.md)|'*函式*' 無法編譯成原生: '*說明*'|  
|編譯器錯誤 C2347|已過時。|  
|[編譯器錯誤 C2348](compiler-error-c2348.md)|'*類型*': 不是 c-style 彙總，無法在內嵌 IDL 中匯出|  
|[編譯器錯誤 C2349](compiler-error-c2349.md)|'*函式*' 無法編譯為 managed: '*說明*'; 使用 #pragma unmanaged|  
|[編譯器錯誤 C2350](compiler-error-c2350.md)|'*識別碼*' 不是靜態成員|  
|[編譯器錯誤 C2351](compiler-error-c2351.md)|過時的 C++ 建構函式初始化語法|  
|[編譯器錯誤 C2352](compiler-error-c2352.md)|'*識別碼*': 非靜態成員函式的呼叫不合法|  
|[編譯器錯誤 C2353](compiler-error-c2353.md)|不能使用例外狀況規格|  
|編譯器錯誤 C2354|已過時。|  
|[編譯器錯誤 C2355](compiler-error-c2355.md)|'this': 只能在非靜態成員函式或非靜態資料成員初始設定式內部參考|  
|[編譯器錯誤 C2356](compiler-error-c2356.md)|在轉譯單位中不需要變更初始化區段|  
|[編譯器錯誤 C2357](compiler-error-c2357.md)|'*識別碼*': 必須是類型的函式'*類型*'|  
|編譯器錯誤 C2358|'*識別碼*': 靜態屬性不能定義在類別定義之外|  
|編譯器錯誤 C2359|已過時。|  
|[編譯器錯誤 C2360](compiler-error-c2360.md)|初始化 '*識別碼*' 會被 'case' 標籤略過|  
|[編譯器錯誤 C2361](compiler-error-c2361.md)|初始化 '*識別碼*' 會被 'default' 標籤略過|  
|[編譯器錯誤 C2362](compiler-error-c2362.md)|初始化 '*識別碼*' 會被略過 ' goto*標籤*'|  
|編譯器錯誤 C2363|編譯器內建數值限制函式需要字串常值引數|  
|[編譯器錯誤 C2364](compiler-error-c2364.md)|'*類型*': 自訂屬性的類型不合法|  
|[編譯器錯誤 C2365](compiler-error-c2365.md)|'*member1*': 重複定義; 先前的定義是'*member2*'|  
|編譯器錯誤 C2366|'*識別碼*': 重複定義; implementation_key 的規範|  
|編譯器錯誤 C2367|已過時。|  
|[編譯器錯誤 C2368](compiler-error-c2368.md)|'*識別碼*': 重複定義; 不同的配置的規範|  
|[編譯器錯誤 C2369](compiler-error-c2369.md)|'*識別碼*': 重複定義; 註標不相同|  
|[編譯器錯誤 C2370](compiler-error-c2370.md)|'*識別碼*': 重複定義; 不同的儲存類別|  
|[編譯器錯誤 C2371](compiler-error-c2371.md)|'*識別碼*': 重複定義; 基本類型不相同|  
|[編譯器錯誤 C2372](compiler-error-c2372.md)|'*識別碼*': 重複定義; 不同類型的間接取值|  
|[編譯器錯誤 C2373](compiler-error-c2373.md)|'*識別碼*': 重複定義; 不同的型別修飾詞|  
|[編譯器錯誤 C2374](compiler-error-c2374.md)|'*識別碼*': 重複定義; 多個初始設定|  
|[編譯器錯誤 C2375](compiler-error-c2375.md)|'*識別碼*': 重複定義; 不同的連結|  
|[編譯器錯誤 C2376](compiler-error-c2376.md)|'*識別碼*': 重複定義; 基礎的配置不相同|  
|[編譯器錯誤 C2377](compiler-error-c2377.md)|'*識別碼*': 重複定義; typedef 無法以其他符號多載|  
|[編譯器錯誤 C2378](compiler-error-c2378.md)|'*識別碼*': 重複定義; 符號無法以 typedef 多載|  
|[編譯器錯誤 C2379](compiler-error-c2379.md)|型式參數*數目*有不同的類型，當升級|  
|[編譯器錯誤 C2380](compiler-error-c2380.md)|型別前置 '*識別碼*' （具有建構函式傳回型別或目前的類別名稱的重新定義不合法？）|  
|[編譯器錯誤 C2381](compiler-error-c2381.md)|'*識別碼*': 重複定義;'__declspec （noreturn）' [[noreturn]]' 不同|  
|[編譯器錯誤 C2382](compiler-error-c2382.md)|'*識別碼*': 重複定義; 不同的例外狀況規格|  
|[編譯器錯誤 C2383](compiler-error-c2383.md)|'*識別碼*': 預設引數不允許在這個符號|  
|[編譯器錯誤 C2384](compiler-error-c2384.md)|'*成員*': 無法套用 thread_local 或 __declspec （thread） 的 managed/WinRT 類別成員|  
|[編譯器錯誤 C2385](compiler-error-c2385.md)|模稜兩可存取的 '*成員*'|  
|[編譯器錯誤 C2386](compiler-error-c2386.md)|'*識別碼*': 目前的範圍中已經有具有此名稱的符號|  
|[編譯器錯誤 C2387](compiler-error-c2387.md)|'*識別碼*': 模稜兩可的基底類別|  
|[編譯器錯誤 C2388](compiler-error-c2388.md)|'*識別碼*': 符號不可同時 （appdomain） 和 __declspec （process） 宣告|  
|[編譯器錯誤 C2389](compiler-error-c2389.md)|'*運算子*': 不合法的運算元 'nullptr'|  
|[編譯器錯誤 C2390](compiler-error-c2390.md)|'*識別碼*': 不正確的儲存類別*規範*'|  
|[編譯器錯誤 C2391](compiler-error-c2391.md)|'*識別碼*': 'friend' 不能在類型定義|  
|[編譯器錯誤 C2392](compiler-error-c2392.md)|'*member1*': covariant 傳回類型不支援在 managed/WinRT 類型中，否則'*member2*' 將會被覆寫|  
|[編譯器錯誤 C2393](compiler-error-c2393.md)|'*符號*': per-appdomain 符號不可配置在區段'*區段*'|  
|[編譯器錯誤 C2394](compiler-error-c2394.md)|'*類型*:: 運算子*運算子*': CLR/WinRT 運算子無效。 至少一個參數必須屬於下列類型: 'T ^'，' T ^ %'，' T ^ （& s) '，其中 T ='*類型*'|  
|[編譯器錯誤 C2395](compiler-error-c2395.md)|'*類型*:: 運算子*運算子*': CLR/WinRT 運算子無效。 至少一個參數必須屬於下列類型: 'T '，' T %'，' T （& s) '，' T ^'，' T ^ %'，' T ^ （& s) '，其中 T ='*類型*'|  
|[編譯器錯誤 C2396](compiler-error-c2396.md)|'*type1*:: 運算子*type2*': CLR/WinRT 使用者定義轉換函式無效。 必須轉換自或轉換成: 'T ^'，' T ^ %'，' T ^ &'，其中 T ='*type1*'|  
|[編譯器錯誤 C2397](compiler-error-c2397.md)|從轉換 '*type1*'to'*type2*' 必須是縮小轉換|  
|編譯器錯誤 C2398|元素 '*數目*': 從'*type1*'to'*type2*' 必須是縮小轉換|  
|編譯器錯誤 C2399|已過時。|  

