---
title: "/QIfist (抑制 _ftol) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/qifist"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "QIfist 編譯器選項 [C++]"
  - "-QIfist 編譯器選項 [C++]"
  - "/QIfist 編譯器選項 [C++]"
ms.assetid: 1afd32a5-f658-4b66-85f4-e0ce4cb955bd
caps.latest.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 17
---
# /QIfist (抑制 _ftol)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在必須從浮點類型轉換為整數類型時，抑制對 Helper 函式 `_ftol` 的呼叫。  
  
## 語法  
  
```  
/QIfist  
```  
  
## 備註  
  
> [!NOTE]
>  **\/QIfist** 僅供以 x86 為目標的編譯器使用；這個編譯器選項不提供以 [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] 或 ARM 為目標的編譯器使用。  
  
 除了從浮點型別轉換為整數型別之外，`_ftol` 函式也會透過設定控制字的第 10 和 11 位元，以確保浮點單位 \(FPU\) 的捨入模式是趨向於零，  這樣可以保證從浮點型別到整數型別的轉換會依據 ANSI C 標準 \(捨去數字的小數部分\) 的描述進行。  使用 **\/QIfist** 時，此一保證即不再適用。  捨入模式必須為 Intel 參考手冊中所載以下四種模式中的某一種：  
  
-   趨向最接近者捨入 \(如果等距離則為偶數\)  
  
-   趨向負無限大捨入  
  
-   趨向正無限大捨入  
  
-   趨向零捨入  
  
 您可以使用 [\_control87、\_controlfp、\_\_control87\_2](../../c-runtime-library/reference/control87-controlfp-control87-2.md) C Run\-Time 函式，修改 FPU 的捨入行為。  FPU 的預設捨入模式為「趨向最接近者捨入」。使用 **\/QIfist** 可以提升應用程式的效能，但是也有風險。  在生產環境中信賴以 **\/QIfist** 建置 \(Build\) 的程式碼之前，您應該先徹底測試程式碼中受捨入模式影響的各個部分。  
  
 [\/arch \(x86\)](../../build/reference/arch-x86.md) 和 **\/QIfist** 不能用於同一個編譯中。  
  
> [!NOTE]
>  **\/QIfist** 並非預設運作，因為捨入位元也會影響浮點而進行浮點捨入 \(這種捨入作業在每次計算之後都會進行\)，所以設定 C\-style \(趨向零\) 捨入的旗標時，浮點計算可能會不同；  如果程式碼依賴預期截斷浮點數小數部分的行為而運作，就不應該使用 **\/QIfist**。  如果不確定，就不要使用 **\/QIfist**。  
  
 **\/QIfist** 已被取代。  編譯器已大幅提升將浮點 \(Float\) 轉換成 int 的速度。  如需詳細資訊，請參閱[Deprecated Compiler Options in Visual C\+\+ 2005](http://msdn.microsoft.com/zh-tw/aa59fce3-50b8-4f66-9aeb-ce09a7a84cce)。  
  
### 在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 \[**屬性頁**\] 對話方塊。  如需詳細資訊，請參閱 [如何：開啟專案屬性頁](../../misc/how-to-open-project-property-pages.md)。  
  
2.  按一下 \[**C\/C\+\+**\] 資料夾。  
  
3.  按一下 \[**命令列**\] 屬性頁。  
  
4.  在 \[**其他選項**\] 方塊中，輸入編譯器選項。  
  
### 若要以程式方式設定這個編譯器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。  
  
## 請參閱  
 [\/Q 選項 \(低階運算\)](../../build/reference/q-options-low-level-operations.md)   
 [編譯器選項](../../build/reference/compiler-options.md)   
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)