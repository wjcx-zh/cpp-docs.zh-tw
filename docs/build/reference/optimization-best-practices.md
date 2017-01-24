---
title: "最佳化最佳作法 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Visual C++，最佳化"
  - "最佳化，最佳作法"
ms.assetid: f3433148-7255-4ca6-8a4f-7c31aac88508
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 最佳化最佳作法
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

本文件說明在 Visual C\+\+ 中進行最佳化的一些最佳做法。  將會討論下列主題：  
  
-   編譯器和連結器選項  
  
    -   特性指引最佳化  
  
    -   應該使用哪一個層級的最佳化？  
  
    -   浮點參數  
  
-   最佳化 Declspec  
  
-   最佳化 Pragma  
  
-   \_\_restrict 和 \_\_assume  
  
-   內建支援  
  
-   例外狀況  
  
## 編譯器和連結器選項  
  
### 特性指引最佳化  
 Visual C\+\+ 支援特性指引最佳化 \(PGO\)。  此最佳化會使用來自於檢測的應用程式版本過去執行的設定檔資料，以驅使未來的應用程式最佳化。  使用 PGO 可能會耗費相當多的時間，所以並不是每位開發人員都會使用它，但是我們建議您在產品的最終發行組建中使用 PGO。  如需詳細資訊，請參閱[特性指引最佳化](../../build/reference/profile-guided-optimizations.md)。  
  
 此外，也已經改善了整個程式最佳化 \(也稱為連結時產生程式碼\) 及 **\/O1** 和 **\/O2** 最佳化。  一般而言，使用其中一個選項所編譯的應用程式將會比使用舊版編譯器編譯的相同應用程式更為快速。  
  
 如需詳細資訊，請參閱[\/GL \(整個程式最佳化\)](../../build/reference/gl-whole-program-optimization.md)與[\/O1、\/O2 \(最小大小、最快速度\)](../../build/reference/o1-o2-minimize-size-maximize-speed.md)。  
  
### 應該使用哪一個層級的最佳化？  
 應該要盡可能在最終的發行組建中使用特性指引最佳化進行編譯；  如果無法使用 PGO 進行建置 \(不論是因為沒有足夠的基礎結構來執行檢測的組建，或是對案例沒有存取權\)，則建議您使用整個程式最佳化來進行建置。  
  
 **\/Gy** 參數也會非常有用，  它會針對每個函式產生個別的 COMDAT，而要移除未參考的 COMDAT 和 COMDAT 摺疊時，會為連結器提供更大的彈性。  使用 **\/Gy** 的唯一缺點是可能會對建置時間有些微的影響；  因此，通常建議使用它。  如需詳細資訊，請參閱[\/Gy \(啟用函式階層連結\)](../../build/reference/gy-enable-function-level-linking.md)。  
  
 若是 64 位元環境中的連結，建議使用 **\/OPT:REF,ICF** 連結器選項；若是在 32 位元環境中，則建議使用 **\/OPT:REF**。  如需詳細資訊，請參閱[\/OPT \(最佳化\)](../../build/reference/opt-optimizations.md)。  
  
 此外，強烈建議您產生偵錯符號，即使是在最佳化的發行組建中亦然；  因為這樣不會影響產生的程式碼，也會讓應用程式的偵錯變得輕鬆許多 \(如果需要進行偵錯\)。  
  
### 浮點參數  
 已移除 **\/Op** 編譯器選項，並加入了下列四個用來處理浮點最佳化的編譯器選項：  
  
|||  
|-|-|  
|**\/fp:precise**|這是預設的建議做法，而在大多數情況下也應該採用。|  
|**\/fp:fast**|如果效能具有極大的重要性 \(例如在電玩中\)，則建議採取這個做法，  如此將會產生最快速的效能。|  
|**\/fp:strict**|如果需要精確的浮點例外狀況和 IEEE 行為，則建議採取這個做法，  如此將會產生最慢的效能。|  
|**\/fp:except\[\-\]**|可以與 **\/fp:strict** 或 **\/fp:precise** 結合使用 \(但是不能與 **\/fp:fast** 結合使用\)。|  
  
 如需詳細資訊，請參閱[\/fp \(指定浮點數行為\)](../../build/reference/fp-specify-floating-point-behavior.md)。  
  
## 最佳化 Declspec  
 在本節中，將會審視在程式中可用來提升效能的兩種 declspec：`__declspec(restrict)` 和 `__declspec(noalias)`。  
  
 `restrict` declspec 只能套用到會傳回指標的函式宣告，例如 `__declspec(restrict) void *malloc(size_t size);`。  
  
 `restrict` declspec 用於傳回沒有別名的指標之函式中。  這個關鍵字用於 C 執行階段程式庫的 `malloc` 實作，因為它絕對不會傳回已經在目前程式中使用的指標值 \(除非您採取了一些不合法的動作，例如在釋放記憶體之後還使用記憶體\)。  
  
 `restrict` declspec 為編譯器提供了更多用來執行編譯器最佳化的資訊；  其中最困難的一件事是要讓編譯器判斷哪些指標會化名為其他指標，而使用這項資訊對於編譯器會有很大的幫助。  
  
 很重要的一點是，這對於編譯器而言是一項承諾，而不是編譯器將會驗證的事項。  如果程式不適當地使用了這個 `restrict` declspec，則程式可能會產生不正確的行為。  
  
 如需詳細資訊，請參閱[restrict](../../cpp/restrict.md)。  
  
 `noalias` declspec 也是一樣只會套用到函式，並指示該函式為半純的函式。  半純的函式是一種只會參考或修改區域變數、引數和引數第一層間接取值的函式。  這個 declspec 是編譯器的一項承諾，而如果此函式參考 Globals 或指標引數的第二層間接取值，則編譯器可能會產生讓應用程式中斷的程式碼。  
  
 如需詳細資訊，請參閱[noalias](../../cpp/noalias.md)。  
  
## 最佳化 Pragma  
 也有好幾個有用的 Pragma 可以讓程式碼最佳化，  這裡所討論的第一個是 `#pragma optimize`：  
  
```  
#pragma optimize("{opt-list}", on | off)  
```  
  
 此 Pragma 可讓您以逐一函式的方式來設定指定的最佳化層級，  這對於在以最佳化編譯指定之函式時發生應用程式損毀的罕見情況，會是很理想的做法。  您可以在單一函式中使用這個做法來停用最佳化：  
  
```  
#pragma optimize("", off)  
int myFunc() {...}  
#pragma optimize("", on)  
```  
  
 如需詳細資訊，請參閱[optimize](../../preprocessor/optimize.md)。  
  
 內嵌是編譯器執行的一個最重要的最佳化作業，這裡將討論一些可修改這項行為的 Pragma。  
  
 `#pragma inline_recursion` 對於指定您是否希望應用程式有能力內嵌遞迴呼叫，將會很實用。  此功能預設為關閉，  如果是小型函式的表層遞迴，則可能要將此功能開啟。  如需詳細資訊，請參閱[inline\_recursion](../../preprocessor/inline-recursion.md)。  
  
 另一個限制內嵌深度的有用 Pragma 為 `#pragma inline_depth`，  這通常對於嘗試限制程式或函式大小的情況會很有用處。  如需詳細資訊，請參閱[inline\_depth](../../preprocessor/inline-depth.md)。  
  
## \_\_restrict 和 \_\_assume  
 Visual C\+\+ 中有兩個關鍵字可以提升效能：[\_\_restrict](../../cpp/extension-restrict.md) 和 [\_\_assume](../../intrinsics/assume.md)。  
  
 首先，應該要注意 `__restrict` 和 `__declspec(restrict)` 兩者是不同的。  這兩者有些相關，但語意不同。  `__restrict` 是型別限定詞，類似 `const` 或 `volatile`，但僅適用於指標型別。  
  
 以 `__restrict` 修改的指標稱為「*\_\_restrict 指標*」\(\_\_restrict Pointer\)，  \_\_restrict 指標是一個只能透過 \_\_restrict 指標加以存取的指標。  換句話說，無法使用另一個指標來存取 \_\_restrict 指標所指向的資料。  
  
 對 Visual C\+\+ 最佳化工具而言，`__restrict` 是功能強大的工具，但請小心使用。  如果使用不當，此最佳化工具可能會執行讓應用程式中斷的最佳化作業。  
  
 `__restrict` 關鍵字取代了舊版的 **\/Oa** 參數。  
  
 開發人員使用了 `__assume,` 之後，即可告知編譯器對某個變數的值做出假設。  
  
 例如，`__assume(a < 5);` 會告知最佳化工具，在變數的該行程式碼上，`a` 小於 5。  這個也是對編譯器的一項承諾。  如果此時在程式中的 `a` 實際上為 6，則編譯器最佳化之後的程式行為可能不會如您所預期。  在 switch 陳述式和 \(或\) 條件運算式之前，最好使用 `__assume`。  
  
 `__assume` 的使用有一些限制；  首先，它只是一個建議，就像 `__restrict` 一樣，所以編譯器可以自由地予以忽略。  此外，`__assume` 目前只能用於針對常數的變數不等比較，  它無法散佈符號式不等比較，例如 assume\(a \< b\)。  
  
## 內建支援  
 內建 \(Intrinsic\) 為函式呼叫，編譯器會在這裡了解有關呼叫的內建資訊；它會針對程式庫中的函式發出程式碼，而不會呼叫該函式。  位於 \<Installation\_Directory\>\\VC\\include\\intrin.h 中的標頭檔 intrin.h 包含了每一個支援平台 \(x86、x64 和 Itanium\) 的所有可用內建。  
  
 內建可讓程式設計人員有能力進入程式碼的更深層，而不需使用組件。  使用內建有好幾個優點：  
  
1.  程式碼會有更高的可移植性，  多個 CPU 架構上有提供數個內建。  
  
2.  程式碼更容易閱讀，因為程式碼仍然是以 C\/C\+\+ 所編寫。  
  
3.  程式碼能夠得到編譯器最佳化的好處；  當編譯器變得更好時，內建的程式碼產生作業也會提升。  
  
 如需詳細資訊，請參閱[編譯器內建](../../intrinsics/compiler-intrinsics.md)與[Benefits of Using Intrinsics](http://msdn.microsoft.com/zh-tw/57af8920-527f-44af-a741-a07cbe80bf02)。  
  
## 例外狀況  
 在使用例外狀況時，會有一些關聯的效能影響。  當使用的 try 區塊會讓編譯器無法執行某些最佳化作業時，即會產生一些限制。  在 x86 平台上，try 區塊會產生額外的效能降低情形，因為在程式碼執行期間，必須產生一些額外的狀態資訊。  在 64 位元平台上，try 區塊不怎麼會降低效能，但是一旦擲回例外狀況後，尋找處理常式及回溯堆疊的過程可能會耗費許多資源。  
  
 因此，建議您除非必要，否則最好不要將 try\/catch 區塊引入程式碼中。  如果您必須使用例外狀況，請盡可能地使用同步例外狀況。  如需詳細資訊，請參閱[結構化例外狀況處理](../../cpp/structured-exception-handling-c-cpp.md)。  
  
 最後一點，只有在異常的情況下才擲回例外狀況；  在一般的控制流程中使用例外狀況，可能會讓效能受到嚴重的影響。  
  
## 請參閱  
 [最佳化程式碼](../../build/reference/optimizing-your-code.md)