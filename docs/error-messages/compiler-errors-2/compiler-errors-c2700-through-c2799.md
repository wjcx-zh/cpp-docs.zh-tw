---
title: "編譯器錯誤 C2700 C2799 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2716
- C2717
- C2727
- C2729
- C2737
- C2740
- C2741
- C2742
- C2744
- C2746
- C2747
- C2759
- C2763
- C2769
- C2772
- C2789
- C2796
- C2799
helpviewer_keywords:
- C2716
- C2717
- C2727
- C2729
- C2737
- C2740
- C2741
- C2742
- C2744
- C2746
- C2747
- C2759
- C2763
- C2769
- C2772
- C2789
- C2796
- C2799
dev_langs:
- C++
ms.assetid: 6ee257bb-94bc-42b9-af2c-3c73926afba4
caps.latest.revision: 13
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
ms.openlocfilehash: 02bfc54853aea219b4ff0a08231e73fb53550a37
ms.lasthandoff: 04/24/2017

---
# <a name="compiler-errors-c2700-through-c2799"></a>編譯器錯誤 C2700 C2799
這部分文件中的文章包含 Visual C++ 編譯器錯誤的子區段的相關資訊。 您可以在此存取資訊，或是在 Visual Studio 的 [ **輸出** ] 視窗，您可以選取錯誤代碼然後選擇 F1 鍵。  
  
> [!NOTE]
>  並非每個[!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)]錯誤會記載於 MSDN 中。 在許多情況下，診斷訊息會提供所有可用的資訊。 如果您認為錯誤訊息需要補充說明，請告訴我們。 您可以使用這個頁面上的回函表單或移至 Visual Studio 中的功能表列並選擇**協助**，**回報 Bug**，或您可以提出建議或 bug 報告上[Microsoft Connect](http://connect.microsoft.com/VisualStudio)。  
  
 您可能會發現其他協助的 MSDN 公共論壇上錯誤及警告。 [Visual c + + 語言](http://go.microsoft.com/fwlink/?LinkId=158195)論壇是關於問題及討論[!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)]語言語法和編譯器。 [Visual c + + 一般](http://go.microsoft.com/fwlink/?LinkId=158194)論壇是關於問題[!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)]其他論壇中沒有討論之。 您也可能會在找到關於錯誤和警告的說明[堆疊溢位](http://stackoverflow.com/)。  
  
|錯誤|訊息|  
|-----------|-------------|  
|[編譯器錯誤 C2700](compiler-error-c2700.md)|'*類型*': 無法擲回 （使用 /w4 以取得詳細資訊中的）|  
|[編譯器錯誤 C2701](compiler-error-c2701.md)|'*函式*': 不可區域類別的 friend 函式範本/泛型。|  
|[編譯器錯誤 C2702](compiler-error-c2702.md)| __except 不可以出現在終止區塊中|  
|[編譯器錯誤 C2703](compiler-error-c2703.md)|不合法的 __leave 陳述式|  
|[編譯器錯誤 C2704](compiler-error-c2704.md)|'*函式*': __va_start 內建只允許在 varargs|  
|[編譯器錯誤 C2705](compiler-error-c2705.md)|'*標籤*': 不合法的跳躍進入'*exception_block*' 範圍|  
|[編譯器錯誤 C2706](compiler-error-c2706.md)|不合法的 __except 沒有相符的 __try (在 __try 區塊中遺漏 '}' ?)|  
|[編譯器錯誤 C2707](compiler-error-c2707.md)|'*識別碼*': 內建函式不正確的內容|  
|[編譯器錯誤 C2708](compiler-error-c2708.md)|'*識別碼*': 實質參數長度 （位元組） 不同於至上一個呼叫或參考|  
|[編譯器錯誤 C2709](compiler-error-c2709.md)|'*識別碼*': 型式參數長度 （位元組） 不同於先前的宣告|  
|[編譯器錯誤 C2710](compiler-error-c2710.md)|'*識別碼*':' __declspec (*修飾詞*)' 只可以套用至傳回指標的函式|  
|[編譯器錯誤 C2711](compiler-error-c2711.md)|'*函式*': 這個函式不可以編譯為 managed，請考慮使用 #pragma unmanaged|  
|[編譯器錯誤 C2712](compiler-error-c2712.md)|無法在需要物件回溯 (Object Unwinding) 的函式中使用 __try|  
|[編譯器錯誤 C2713](compiler-error-c2713.md)|每個函式只允許一種例外狀況處理形式|  
|[編譯器錯誤 C2714](compiler-error-c2714.md)|不可使用 alignof(void)|  
|[編譯器錯誤 C2715](compiler-error-c2715.md)|'*類型*': 無法擲回或攔截這種類型|  
|編譯器錯誤 C2716|已過時。|  
|編譯器錯誤 C2717|已過時。|  
|[編譯器錯誤 C2718](compiler-error-c2718.md)|'*類型*': 要求對齊的實質參數*數目*將不會對齊|  
|[編譯器錯誤 C2719](compiler-error-c2719.md)|'*參數*': 要求對齊的型式參數*數目*將不會對齊|  
|[編譯器錯誤 C2720](compiler-error-c2720.md)|'*識別碼*':'*規範*' 儲存類別規範不合法成員上|  
|[編譯器錯誤 C2721](compiler-error-c2721.md)|'*規範*': 不合法的運算子關鍵字和型別之間的儲存類別規範|  
|[編譯器錯誤 C2722](compiler-error-c2722.md)|'::*運算子*': 跟隨的運算子命令不合法; 請改用 ' 運算子*運算子*'|  
|[編譯器錯誤 C2723](compiler-error-c2723.md)|'*函式*':'*規範*' 規範不合法的函式定義上|  
|[編譯器錯誤 C2724](compiler-error-c2724.md)|'*函式*': 'static' 不應該使用以檔案範圍定義的成員函式|  
|[編譯器錯誤 C2725](compiler-error-c2725.md)|'*類型*': 無法擲回或攔截由值或參考的 managed/WinRT 物件|  
|[編譯器錯誤 C2726](compiler-error-c2726.md)|'gcnew' 只可用來建立具有 managed/WinRT 類型的物件|  
|編譯器錯誤 C2727|已過時。|  
|[編譯器錯誤 C2728](compiler-error-c2728.md)|'*類型*': 原生陣列不可包含這個類型|  
|編譯器錯誤 C2729|已過時。|  
|[編譯器錯誤 C2730](compiler-error-c2730.md)|'*類別*': 不可為它自己的基底類別|  
|[編譯器錯誤 C2731](compiler-error-c2731.md)|'*函式*': 無法多載函式|  
|[編譯器錯誤 C2732](compiler-error-c2732.md)|連結規格和先前的規格衝突 '*函式*'|  
|[編譯器錯誤 C2733](compiler-error-c2733.md)|'*函式*': 不允許的多載函式的 C 連結的第二個|  
|[編譯器錯誤 C2734](compiler-error-c2734.md)|'*識別碼*': 必須初始化 'const' 的物件，如果不是 'extern'|  
|[編譯器錯誤 C2735](compiler-error-c2735.md)|'*關鍵字*' 在型式參數類型規範中不允許關鍵字|  
|[編譯器錯誤 C2736](compiler-error-c2736.md)|'*關鍵字*' 轉換中不允許關鍵字|  
|編譯器錯誤 C2737|'*識別碼*': 必須初始化 'constexpr' 物件|  
|[編譯器錯誤 C2738](compiler-error-c2738.md)|'運算子*類型*': 模稜兩可，或不是成員的'*類別*'|  
|[編譯器錯誤 C2739](compiler-error-c2739.md)|'*數目*': 明確的 managed/WinRT 陣列維度必須是介於 1 到 32 之間|  
|編譯器錯誤 C2740|運算元的值 '*數目*'超出範圍'*lower_bound* - *upper_bound*'|  
|編譯器錯誤 C2741|框架大小太大|  
|編譯器錯誤 C2742|已過時。|  
|[編譯器錯誤 C2743](compiler-error-c2743.md)|'*類型*': 無法攔截原生類型具有 __clrcall 解構函式或複製建構函式|  
|編譯器錯誤 C2744|'*運算子*' 不是有效的 CLR/WinRT 運算子|  
|[編譯器錯誤 C2745](compiler-error-c2745.md)|'*語彙基元*': 這個語彙基元無法轉換為識別項|  
|編譯器錯誤 C2746|已過時。|  
|編譯器錯誤 C2747|已過時。|  
|[編譯器錯誤 C2748](compiler-error-c2748.md)|建立 managed/WinRT 陣列必須有陣列大小或陣列初始設定式|  
|[編譯器錯誤 C2749](compiler-error-c2749.md)|'*類型*': 只能擲回或攔截 managed 類別以 /clr: safe 的控制代碼|  
|[編譯器錯誤 C2750](compiler-error-c2750.md)|'*類型*': 不能使用 'new'，參考上的類型; 請用 'gcnew' 代替|  
|[編譯器錯誤 C2751](compiler-error-c2751.md)|'*參數*': 不限定函式參數的名稱|  
|[編譯器錯誤 C2752](compiler-error-c2752.md)|'*範本*': 一個以上的部分特製化符合樣板引數清單|  
|[編譯器錯誤 C2753](compiler-error-c2753.md)|'*範本*': 部分特製化不能符合主要樣板的引數清單|  
|[編譯器錯誤 C2754](compiler-error-c2754.md)|'*範本*': 部分特製化不能有相依的非類型樣板參數|  
|[編譯器錯誤 C2755](compiler-error-c2755.md)|'*參數*': 部分特製化非類型參數必須是簡單識別項|  
|[編譯器錯誤 C2756](compiler-error-c2756.md)|'*範本*': 預設範本引數的部分特製化上不允許|  
|[編譯器錯誤 C2757](compiler-error-c2757.md)|'*識別碼*': 已經有具有此名稱的符號，因此無法使用此名稱做為命名空間名稱|  
|[編譯器錯誤 C2758](compiler-error-c2758.md)|'*成員*': 必須初始化參考類型的成員|  
|編譯器錯誤 C2759|內嵌組合語言報告︰ *error_message*|  
|[編譯器錯誤 C2760](compiler-error-c2760.md)|語法錯誤︰ 必須是 '*token1*'not'*token2*'|  
|[編譯器錯誤 C2761](compiler-error-c2761.md)|'*函式*': 不允許成員函式重新宣告|  
|[編譯器錯誤 C2762](compiler-error-c2762.md)|'*範本*': 無效的運算式當做樣板引數'*參數*'|  
|編譯器錯誤 C2763|'*範本*': 無效的字串常值做為樣板引數使用'*參數*'|  
|[編譯器錯誤 C2764](compiler-error-c2764.md)|'*參數*': 沒有使用或無法推算在部分特製化的樣板參數'*特製化*'|  
|[編譯器錯誤 C2765](compiler-error-c2765.md)|'*函式*': 函式樣板的明確特製化不能有任何預設引數|  
|[編譯器錯誤 C2766](compiler-error-c2766.md)|明確特製化;'*特製化*' 已經定義|  
|[編譯器錯誤 C2767](compiler-error-c2767.md)|managed/WinRT 陣列維度不相符︰ 預期*數目*引數-*數目*提供|  
|[編譯器錯誤 C2768](compiler-error-c2768.md)|'*函式*': 不合法使用明確樣板引數|  
|編譯器錯誤 C2769|您無法大括號初始化基底/成員初始設定式清單中的 managed/WinRT 陣列|  
|[編譯器錯誤 C2770](compiler-error-c2770.md)|無效的明確範本/泛型引數 '*範本*'|  
|[編譯器錯誤 C2771](compiler-error-c2771.md)|#匯入只允許在全域或命名空間範圍|  
|編譯器錯誤 C2772|已過時。|  
|[編譯器錯誤 C2773](compiler-error-c2773.md)|#匯入和 #using 只適用於 c + + 編譯器|  
|[編譯器錯誤 C2774](compiler-error-c2774.md)|'*識別碼*': 不 'put' 方法，這個屬性與相關聯|  
|[編譯器錯誤 C2775](compiler-error-c2775.md)|'*識別碼*': 不 'get' 方法，這個屬性與相關聯|  
|[編譯器錯誤 C2776](compiler-error-c2776.md)|每個屬性只可以指定一個 'get' 方法|  
|[編譯器錯誤 C2777](compiler-error-c2777.md)|每個屬性只可以指定一個 'put' 方法|  
|[編譯器錯誤 C2778](compiler-error-c2778.md)|__declspec(uuid()) 產生的 GUID 不適當|  
|[編譯器錯誤 C2779](compiler-error-c2779.md)|'*宣告*': 只能和非靜態資料成員相關聯的屬性方法|  
|[編譯器錯誤 C2780](compiler-error-c2780.md)|'*宣告*': 必須要有*數目*引數-*數目*提供|  
|[編譯器錯誤 C2781](compiler-error-c2781.md)|'*宣告*': 必須要有至少*數目*引數-*數目*提供|  
|[編譯器錯誤 C2782](compiler-error-c2782.md)|'*宣告*': 範本/泛型參數'*參數*' 模稜兩可|  
|[編譯器錯誤 C2783](compiler-error-c2783.md)|'*宣告*': 無法推算範本/泛型引數'*識別碼*'|  
|[編譯器錯誤 C2784](compiler-error-c2784.md)|'*宣告*': 無法推算範本/泛型引數'*type1*'from'*type2*'|  
|[編譯器錯誤 C2785](compiler-error-c2785.md)|'*declaration1*'和'*declaration2*' 的傳回類型不同|  
|[編譯器錯誤 C2786](compiler-error-c2786.md)|'*類型*': __uuidof 的運算元無效|  
|[編譯器錯誤 C2787](compiler-error-c2787.md)|'*識別碼*': 沒有 GUID 已經與此物件相關聯|  
|[編譯器錯誤 C2788](compiler-error-c2788.md)|'*識別碼*': 與此物件相關聯的一個以上的 GUID|  
|編譯器錯誤 C2789|'*識別碼*': 必須初始化 const 限定類型的物件|  
|[編譯器錯誤 C2790](compiler-error-c2790.md)|'super': 此關鍵字只在類別成員函式的主體使用|  
|[編譯器錯誤 C2791](compiler-error-c2791.md)|不合法使用 'super': '*類別*' 並沒有任何基底類別|  
|[編譯器錯誤 C2792](compiler-error-c2792.md)|'super': 此關鍵字之後必須跟隨 '::'|  
|[編譯器錯誤 C2793](compiler-error-c2793.md)|'*語彙基元*': 非預期的語彙基元下列 ':: '、 識別碼或關鍵字 'operator' 必須是|  
|[編譯器錯誤 C2794](compiler-error-c2794.md)|'*識別碼*': 不是任何直接或間接基底類別的成員'*類別*'|  
|[編譯器錯誤 C2795](compiler-error-c2795.md)|'super::*識別碼*' 不是成員函式|  
|編譯器錯誤 C2796|'ref new' 只可用來建立 WinRT 類型的執行個體|  
|[編譯器錯誤 C2797](compiler-error-c2797.md)|（已過時）'*識別碼*': 未實作成員初始設定式清單或非靜態資料成員初始設定式清單初始化|  
|[編譯器錯誤 C2798](compiler-error-c2798.md)|'super::*識別碼*' 模稜兩可|  
|編譯器錯誤 C2799|'*識別碼*': 必須初始化常數限定類別類型沒有使用者提供的預設建構函式的物件|  

