---
title: "/kernel (建立核心模式二進位檔) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/kernel"
  - "/kernel-"
dev_langs: 
  - "C++"
ms.assetid: 6d7fdff0-c3d1-4b78-9367-4da588ce8b05
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /kernel (建立核心模式二進位檔)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

建立可在 Windows 核心執行的二進位檔。  
  
## 語法  
  
```  
/kernel[-]  
```  
  
## Arguments  
 **\/kernel**  
 目前專案中的程式碼已經編譯，並使用一組指定程式碼在核心模式中執行的 C\+\+ 語言規則來做連結。  
  
 **\/kernel\-**  
 目前專案中的程式碼已經編譯，且不使用一組指定程式碼在核心模式中執行的 C\+\+ 語言規則來做連結。  
  
## 備註  
 沒有控制這個選項的 `#pragma` 對應項。  
  
 指定 **\/kernel** 選項會通知編譯器和連結器仲裁哪些語言功能是可允許的核心模式，並確定該您有足夠的表現功能避免核心模式 C\+\+ 特有的執行階段不穩定。  這項作業不允許使用完成 C\+\+ 是受到干擾在核心模式和透過提供警告為 C\+\+ 語言功能可能破壞性的語言功能，但是不能停用。  
  
 **\/kernel** 選項會套用至組建的編譯器和連結器階段，並設定在專案層級。  透過 **\/kernel** 參數指示產生二進位檔的編譯器在連接之後，應該於 Windows 核心載入。  編譯器會使範圍 C\+\+ 語言功能窄與核心相容的子集。  
  
 當 **\/kernel** 時，下表列出編譯器行為的變更。  
  
|行為類型|**\/kernel**的行為|  
|----------|---------------------|  
|C\+\+ 例外狀況處理|停用。  `throw` 與 `try` 關鍵字的所有執行個體發出編譯器錯誤 \(除了例外狀況規格為 `throw()`\)。  除了 **\/EH\-**之外，沒有 **\/EH** 選項與 **\/kernel** 相容。|  
|RTTI|停用。  除非以靜態方式，使用 `dynamic_cast` `dynamic_cast` 和 `typeid` 關鍵字的所有執行個體發出編譯器錯誤。|  
|`new` 和 `delete`|您必須明確定義 `new()` 或 `delete()` 運算子；編譯器和執行階段不會提供一個預設定義。|  
  
 當您使用 **\/kernel** 選項時，自訂呼叫慣例， [\/GS](../../build/reference/gs-buffer-security-check.md) 建置選項和所有最佳化之中。  內嵌不受 **\/kernel**的主要影響，與由編譯器所接受的相同語意。  如果您要確定，內嵌限定詞的 `__forceinline` 接受，您必須確定，啟用警告 [C4714](../../error-messages/compiler-warnings/compiler-warning-level-4-c4714.md) ，讓您知道特定 `__forceinline` 函式時沒有內嵌。  
  
 當編譯器在 **\/kernel** 參數時，它會定義名為 `_KERNEL_MODE` 且具有值 **1**的前置處理器巨集。  您可以使用此條件式編譯以程式碼執行環境是否在使用者模式或核心模式。  例如，下列程式碼指定類別應該在不可分頁的記憶體時，會為核心模式執行時編譯。  
  
```cpp  
#ifdef _KERNEL_MODE  
#define NONPAGESECTION __declspec(code_seg("$kerneltext$"))  
#else  
#define NONPAGESECTION  
#endif  
  
class NONPAGESECTION MyNonPagedClass  
{  
  
};  
  
```  
  
 當搭配 **\/kernel**使用時，有些目標架構和 **\/arch** 選項的下列組合會產生錯誤：  
  
-   **\/arch:{SSE&#124;SSE2&#124;AVX}** 不支援於 x86 上。  **\/arch:IA32** 只支援具有 x86 的 **\/kernel** 。  
  
-   **\/arch:AVX** 不支援在 x64 的 **\/kernel** 。  
  
 與 **\/kernel** 相關聯的建置也將傳遞 **\/kernel** 至連結器。  以下是對連結器行為的影響：  
  
-   累積連接已停用。  如果您將 **\/incremental** 加入至命令列，連結器就會發出這個嚴重錯誤：  
  
     **LINK : fatal error LNK1295: '\/INCREMENTAL' not compatible with '\/KERNEL' specification; link without '\/INCREMENTAL'**  
  
-   連結器會檢查每個目的檔 \(或在靜態程式庫的任何包括封存的成員\) ，以查看是否可以透過使用 **\/kernel** 選項來編譯，但事實並非如此。  如果任何執行個體符合標準，如下表所示，連結器仍然會成功連結，但可能會發出警告。  
  
    ||**\/kernel**物件|**\/kernel\-** 物件、MASM 物件或 cvtresed|**\/kernel** 物件和 **\/kernel\-** 物件的混合|  
    |-|--------------------|-----------------------------------------|-------------------------------------------|  
    |**link \/kernel**|有|有|與警告 LNK4257|  
    |**link**|有|有|有|  
  
     **LNK4257 linking object not compiled with \/KERNEL ; image may not run**  
  
 **\/kernel** 選項與 **\/driver** 選項獨立運作，也不會影響其他選項。  
  
### 若要在 Visual Studio 中設定 \/kernel 編譯器選項  
  
1.  開啟專案的 \[**屬性頁**\] 對話方塊。  如需詳細資訊，請參閱[如何：開啟專案屬性頁](../../misc/how-to-open-project-property-pages.md)。  
  
2.  選取 \[**C\/C\+\+**\] 資料夾。  
  
3.  選取 \[**命令列**\] 屬性頁。  
  
4.  在 \[**其他選項。**\] 方塊中新增 `/kernel` 或 `/kernel-`。  
  
## 請參閱  
 [編譯器選項](../../build/reference/compiler-options.md)   
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)