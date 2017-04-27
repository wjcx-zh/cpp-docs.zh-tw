---
title: "編譯器警告 C4800 透過 C4999 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4806
- C4807
- C4810
- C4811
- C4812
- C4813
- C4816
- C4817
- C4822
- C4825
- C4827
- C4872
- C4880
- C4881
- C4882
- C4900
- C4910
- C4912
- C4913
- C4916
- C4918
- C4920
- C4921
- C4925
- C4926
- C4932
- C4934
- C4935
- C4936
- C4937
- C4938
- C4939
- C4944
- C4947
- C4950
- C4951
- C4952
- C4953
- C4954
- C4955
- C4956
- C4957
- C4958
- C4959
- C4960
- C4961
- C4962
- C4963
- C4966
- C4970
- C4971
- C4972
- C4973
- C4974
- C4981
- C4985
- C4987
- C4988
- C4989
- C4990
- C4991
- C4992
- C4997
- C4998
- C4999
- C4808
- C4809
dev_langs:
- C++
ms.assetid: c3182430-8b3b-4ab2-a532-5cd436707dc8
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: 4bac7b2942f9d72674b8092dc7bf64174dd3c349
ms.openlocfilehash: ac03a99c1a9413b697b6e40101bf1c3e2be9a3a6
ms.lasthandoff: 04/24/2017

---
# <a name="compiler-warnings-c4800-through-c4999"></a>編譯器警告 C4800 透過 C4999
這一部分的文件中的文章包含 Visual c + + 編譯器警告的資訊子集。 您可以在此存取資訊或者，在 Visual Studio 中的 輸出 視窗中，您可以選取錯誤代碼，然後按下 F1 鍵。  
  
> [!NOTE]
>  並非每個[!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)]錯誤或警告會記載於 MSDN 中。 在許多情況下，診斷訊息會提供所有可用的資訊。 如果您認為錯誤訊息需要補充說明，請告訴我們。 您可以使用這個頁面上的回函表單或移至 Visual Studio 中的功能表列並選擇**協助**，**回報 Bug**，或您可以提出建議或 bug 報告上[Microsoft Connect](http://connect.microsoft.com/VisualStudio)。  
  
您可能會發現其他協助的 MSDN 公共論壇上錯誤及警告。 [Visual c + + 語言](http://go.microsoft.com/fwlink/?LinkId=158195)論壇是關於問題及討論[!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)]語言語法和編譯器。 [Visual c + + 一般](http://go.microsoft.com/fwlink/?LinkId=158194)論壇是關於問題[!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)]其他論壇中沒有討論之。 您也可能會在找到關於錯誤和警告的說明[堆疊溢位](http://stackoverflow.com/)。  
  
## <a name="in-this-section"></a>本章節內容  
  
|警告|訊息|  
|-------------|-------------|  
|[編譯器警告 (層級 3) C4800](../../error-messages/compiler-warnings/compiler-warning-level-3-c4800.md)|'type': 值強制設 bool 'true' 或 'false' （效能警告）|  
|[編譯器警告 (層級 1) C4803](../../error-messages/compiler-warnings/compiler-warning-level-1-c4803.md)|'method': 產生的方法具有不同的儲存類別不同的事件 'event'|  
|[編譯器警告 (層級 1) C4804](../../error-messages/compiler-warnings/compiler-warning-level-1-c4804.md)|'operation': 不安全的類型 'bool' 作業中使用|  
|[編譯器警告 (層級 1) C4805](../../error-messages/compiler-warnings/compiler-warning-level-1-c4805.md)|'operation': 不安全的混用類型 'type' 和類型 'type' 中的作業|  
|編譯器警告 （層級 1） C4806|'operation': 不安全的作業︰ 類型 'type' 升級為類型 'type' 沒有值可以等於所給的常數|  
|編譯器警告 （層級 1） C4807|'operation': 不安全混用類型 'type' 和類型 'type' 的帶正負號的位元欄位|  
|編譯器警告 （層級 1） C4808|case 'value' 不是類型的有效 'bool' 切換條件的值|  
|編譯器警告 （層級 1） C4809|switch 陳述式有重複的 'default' 標籤; 已提供所有可能的 'case' 標籤|  
|編譯器警告 （層級 1） C4810|pragma pack(show) 的值 == n|  
|編譯器警告 （層級 1） C4811|pragma conform(forScope, show) 的值 == value|  
|編譯器警告 （層級 1） C4812|過時的宣告樣式：請用 'new_syntax' 代替|  
|編譯器警告 （層級 1） C4813|'function': 區域類別的 friend 函式必須先前已宣告|  
|編譯器警告 （層級 4） C4816|'param': 參數具有大小為零的陣列 （除非物件傳址方式傳遞） 將被截斷的|  
|編譯器警告 （層級 1） C4817|'member': 不合法使用 '。 ' 存取這個成員。編譯器 '->' 取代|  
|[編譯器警告 (層級 1) C4819](../../error-messages/compiler-warnings/compiler-warning-level-1-c4819.md)|檔案包含無法在目前字碼頁 (數字) 中表示的字元。 若要避免資料遺失 Unicode 格式儲存檔案|  
|[編譯器警告 (層級 4) C4820](../../error-messages/compiler-warnings/compiler-warning-level-4-c4820.md)|在成員建構 'member_name' 之後加入 'bytes' 位元組填補|  
|[編譯器警告 (層級 1) C4821](../../error-messages/compiler-warnings/compiler-warning-level-1-c4821.md)|無法判斷 Unicode 編碼類型，請用簽章 (BOM) 儲存檔案|  
|編譯器警告 （層級 1） C4822|'member function': 區域類別成員函式沒有主體|  
|[編譯器警告 (層級 3) C4823](../../error-messages/compiler-warnings/compiler-warning-level-3-c4823.md)|'function': 使用 pin 指標但回溯語意不會啟用。 請考慮使用 /EHa|  
|編譯器警告 （層級 4） C4825||  
|編譯器警告 （層級 3） C4827|具有 0 個參數的公用 'ToString' 方法應該標記為虛擬或覆寫|  
|[編譯器警告 (層級 1) C4829](../../error-messages/compiler-warnings/compiler-warning-level-1-c4829.md)|函式 main 的參數可能不正確。 請考慮 ' int main (platform:: array\<platform:: string ^ > ^ argv)'|  
|[編譯器警告 (層級 1) C4835](../../error-messages/compiler-warnings/compiler-warning-level-1-c4835.md)|'variable': 匯出資料的初始設定式將不會執行，直到主機組件中第一次執行受管理的程式碼|  
|[編譯器警告 (層級 1) C4838](../../error-messages/compiler-warnings/compiler-warning-level-1-c4838.md)|從 'type_1' 轉換為 'type_2' 必須是縮小轉換|  
|[編譯器警告 C4867](../../error-messages/compiler-warnings/compiler-warning-c4867.md)|'function': 函式呼叫遺漏引數清單。使用 '呼叫' 建立成員的指標|  
|[編譯器警告 C4868](../../error-messages/compiler-warnings/compiler-warning-c4868.md)|'file(line_number)' 編譯器不會強制執行括號初始設定清單中的左到右評估順序|  
|編譯器警告 （層級 2） C4872|為 concurrency::parallel_for_each 編譯呼叫圖表時，偵測到浮點除數為零: '%s'|  
|編譯器警告 （層級 1） C4880|從 'const type_1' 轉換成 'type_2': 轉型常數性的指標或參考可能會導致未定義的行為在 amp 限制函式|  
|編譯器警告 （層級 4） C4881|建構函式和 （或） 解構函式將不會叫用 tile_static 變數 'variable'|  
|編譯器警告 （層級 1） C4882|將具有非常數呼叫運算子的函式傳遞給 concurrency::parallel_for_each 的方式已被取代|  
|編譯器警告 C4900|'Tool1' 版本 'version1' 和 'tool2' 版本 'version2' 之間的 Il 不符|  
|[編譯器警告 (層級 1) C4905](../../error-messages/compiler-warnings/compiler-warning-level-1-c4905.md)|寬字串常值轉換成 'LPSTR'|  
|[編譯器警告 (層級 1) C4906](../../error-messages/compiler-warnings/compiler-warning-level-1-c4906.md)|字串常值轉換成 'LPWSTR'|  
|編譯器警告 （層級 1） C4910|'\<識別碼 >: '__declspec （dllexport）' 和 'extern' 不相容的明確具現化|  
|編譯器警告 （層級 1） C4912|'attribute': 屬性在巢狀 UDT 上有未定義的行為，可能受到忽略|  
|編譯器警告 （層級 4） C4913|使用者定義的二進位運算子 ',' 存在，但沒有多載可以轉換所有的運算元，使用預設的內建二進位運算子 ','|  
|編譯器警告 （層級 1） C4916|為了有 dispid，'%$S': 必須由介面引入|  
|[編譯器警告 (層級 1) C4917](../../error-messages/compiler-warnings/compiler-warning-level-1-c4917.md)|'declarator': GUID 僅能與類別、 介面或命名空間相關聯|  
|編譯器警告 （層級 4） C4918|'character': 在 pragma 最佳化清單中有無效的字元|  
|編譯器警告 （層級 1） C4920|enum 列舉成員 member_1 = value_1 已經出現在 enum 列舉為 member_2 = value_2|  
|編譯器警告 （層級 3） C4921|'%s': 不應多次指定屬性值 '%s'|  
|編譯器警告 （層級 1） C4925|'method': 不可以從指令碼呼叫 dispinterface 方法|  
|編譯器警告 （層級 1） C4926|'identifier': 已定義符號：忽略屬性|  
|[編譯器警告 (層級 1) C4927](../../error-messages/compiler-warnings/compiler-warning-level-1-c4927.md)|不合法的轉換; 已經隱含套用一個以上的使用者定義的轉換|  
|[編譯器警告 (層級 1) C4928](../../error-messages/compiler-warnings/compiler-warning-level-1-c4928.md)|不合法的 copy-initialization; 已經隱含套用一個以上的使用者定義的轉換|  
|[編譯器警告 (層級 1) C4929](../../error-messages/compiler-warnings/compiler-warning-level-1-c4929.md)|'file': 類型程式庫包含聯集。忽略 'embedded_idl' 限定詞|  
|[編譯器警告 (層級 1) C4930](../../error-messages/compiler-warnings/compiler-warning-level-1-c4930.md)|'原型': 未呼叫原型函式 （是變數定義？）|  
|[編譯器警告 (層級 4) C4931](../../error-messages/compiler-warnings/compiler-warning-level-4-c4931.md)|我們假設已針對 number 位元指標建置類型程式庫|  
|編譯器警告 （層級 4） C4932|__identifier （identifier) 和\__identifier(identifier) 是否|  
|編譯器警告 （層級 1） C4934|'__delegate(multicast)' 已被取代，請使用 '\__delegate' 改為|  
|編譯器警告 （層級 1） C4935|使用 'access' 修改組件的存取規範|  
|編譯器警告 （層級 1） C4936|以 /clr 或 /clr:pure 編譯時才支援這個 __declspec|  
|編譯器警告 （層級 4） C4937|難以辨別 'text1' 和 'text2' 是否為 'directive' 的引數|  
|編譯器警告 （層級 4） C4938|'var': 浮點削減變數可能會造成不一致的結果，在 /fp: strict 或 #pragma fenv_access 之下|  
|編譯器警告 C4939|#pragma vtordisp 已被取代，將在未來的 Visual c + + 版本中移除|  
|編譯器警告 （層級 1） C4944|'symbol': 無法匯入從 'assembly1' 的符號︰ 因為在目前範圍中已經有 'symbol'|  
|[編譯器警告 (層級 1) C4945](../../error-messages/compiler-warnings/compiler-warning-level-1-c4945.md)|'symbol': 無法匯入從 'assembly1' 的符號︰ 因為 'symbol' 已匯入從另一個組件 'assembly2'|  
|[編譯器警告 (層級 1) C4946](../../error-messages/compiler-warnings/compiler-warning-level-1-c4946.md)|在關聯的類別之間使用的 reinterpret_cast：'class1' 和 'class2'|  
|編譯器警告 （層級 1） C4947|'type_or_member': 標記為過時|  
|[編譯器警告 (層級 2) C4948](../../error-messages/compiler-warnings/compiler-warning-level-2-c4948.md)|'accessor' 的傳回型別不符合對應 setter 的最後一個參數類型|  
|[編譯器警告 (層級 1 和層級 4) C4949](../../error-messages/compiler-warnings/compiler-warning-level-1-and-level-4-c4949.md)|pragma 'managed' 和 'unmanaged' 時才有意義的編譯 ' / /clr [: 選項]'|  
|編譯器警告 （層級 1） C4950|'type_or_member': 標記為過時|  
|編譯器警告 C4951|由於已收集設定檔資料，因此 'function' 已編輯，但未使用函式設定檔資料|  
|編譯器警告 C4952|'function': 在程式資料庫 'pgd_file' 中找到任何分析資料|  
|編譯器警告 C4953|已經編輯內嵌 'function'，因為已收集的分析資料，未使用分析資料|  
|編譯器警告 C4954|'function': 未分析 （包含 __int64 switch 運算式）|  
|編譯器警告 C4955|'import2': 忽略; 匯入已從 'import1' 匯入|  
|編譯器警告 （層級 1） C4956|'type': 這個類型不是可驗證|  
|編譯器警告 （層級 1） C4957|'cast': 從 '從 '轉換成運算 'cast_to' 的明確轉換不是可驗證|  
|編譯器警告 （層級 1） C4958|'operation': 指標算術不是可驗證|  
|編譯器警告 （層級 1） C4959|無法在 /clr: safe 中定義 unmanaged 的類型 'type'，因為存取它的成員會產生無法驗證程式碼|  
|編譯器警告 C4960|'function' 太大而無法分析|  
|編譯器警告 C4961|沒有任何分析資料合併到 '.pgd 檔' 中，特性指引最佳化已停用|  
|編譯器警告 C4962|'function': 特性指引最佳化已停用，因為最佳化導致分析資料變成不一致|  
|編譯器警告 C4963|%s ': 找到沒有設定檔資料在檢測建置中使用了不同的編譯器選項|  
|[編譯器警告 (層級 1) C4964](../../error-messages/compiler-warnings/compiler-warning-level-1-c4964.md)|未指定最佳化選項，將不會收集內部分析|  
|[編譯器警告 (層級 1) C4965](../../error-messages/compiler-warnings/compiler-warning-level-1-c4965.md)|整數 0 的隱含 Box，請使用 nullptr 或明確轉型|  
|編譯器警告 C4966|'%s' 有 __code_seg 註釋，其中含有不支援的區段名稱，註釋已忽略|  
|編譯器警告 C4970|委派建構函式: 目標物件已忽略，因為 '%$pS' 為靜態|  
|編譯器警告 （層級 1） C4971|引數的順序︰\<目標物件 >，\<目標函式 > 委派建構函式已被取代，請使用\<目標函式 >，\<目標物件 ="">|  
|編譯器警告 （層級 1） C4972|直接修改或將 Unbox 作業的結果視為左值，將無法驗證|  
|編譯器警告 C4973|'%$S': 標記為已被取代|  
|編譯器警告 C4974|'%$S': 標記為已被取代|  
|編譯器警告 C4981|Warbird: 標記為 __forceinline 的函式 '%$pD' 無法內嵌，因為它包含例外狀況語意|  
|編譯器警告 （層級 3） C4985|符號名稱 ': 屬性不存在先前的宣告。|  
|[編譯器警告 C4986](../../error-messages/compiler-warnings/compiler-warning-c4986.md)|'%$pS': 例外狀況規格與上一個宣告不符|  
|編譯器警告 （層級 4） C4987|使用非標準的擴充：'throw (...)'|  
|編譯器警告 （層級 4） C4988|'%$S': 變數已在類別/函式範圍外宣告|  
|編譯器警告 C4989|'%s': 類型含有衝突的定義。|  
|編譯器警告 C4990|Warbird: %s|  
|編譯器警告 C4991|Warbird: 標記為 __forceinline 的函式 '%$pD' 無法內嵌，因為內嵌項的保護層級大於父代|  
|編譯器警告 C4992|Warbird: 標記為 __forceinline 的函式 '%$pD' 無法內嵌，因為它包含無法保護的內嵌組譯碼|  
|[編譯器警告 (層級 3) C4995](../../error-messages/compiler-warnings/compiler-warning-level-3-c4995.md)|'function': 名稱被標示為已被取代的 #pragma|  
|[編譯器警告 (層級 3) C4996](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md)|'%$pS': %$*|  
|編譯器警告 （層級 1） C4997|'class': coclass 未實作 COM 介面或虛擬介面|  
|編譯器警告 （層級 1） C4998|例外狀況失敗: %s(%d)|  
|編譯器警告 C4999|未知的警告%$N請選擇 Visual C++ [說明]5D; 功能表上的 [技術支援]5D; 命令，%$N或開啟技術支援檔案以取得更多資訊|
