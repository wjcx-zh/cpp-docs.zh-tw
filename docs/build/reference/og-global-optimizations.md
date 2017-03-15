---
title: "/Og (全域最佳化) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCCLCompilerTool.GlobalOptimizations"
  - "/og"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/Og 編譯器選項 [C++]"
  - "自動暫存器配置"
  - "通用子運算式刪除"
  - "全域最佳化編譯器選項 [C++]"
  - "迴圈結構, 最佳化"
  - "Og 編譯器選項 [C++]"
  - "-Og 編譯器選項 [C++]"
ms.assetid: d10630cc-b9cf-4e97-bde3-8d7ee79e9435
caps.latest.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 14
---
# /Og (全域最佳化)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

提供區域和全域最佳化、自動暫存器配置以及迴圈最佳化。  已取代。  
  
## 語法  
  
```  
/Og  
```  
  
## 備註  
 下列是可用的最佳化：  
  
-   區域和全域通用子運算式 \(Subexpression\) 刪除  
  
     在這項最佳化中，通用子運算式的值只會被計算一次。  在下列範例中，如果 `b` 和 `c` 的值在三個運算式中沒有變更，編譯器可以將  `b + c`  計算指派給一個暫時變數，並且用這個變數代替 `b + c`：  
  
    ```  
    a = b + c;  
    d = b + c;  
    e = b + c;  
    ```  
  
     對於區域通用子運算式最佳化，編譯器會檢查程式碼的短區段中有沒有通用子運算式。  對於全域通用子運算式最佳化，編譯器會搜尋整個函式中有沒有通用子運算式。  
  
-   自動暫存器配置  
  
     這項最佳化會讓編譯器將常用的變數和子運算式儲存在暫存器中；`register` 關鍵字會被忽略。  
  
-   迴圈最佳化  
  
     這項最佳化會從迴圈主體中移除不變量子運算式。  理想的迴圈應該只包含值會隨著每次迴圈執行而改變的運算式。  在下列範例中，運算式  `x + y`  並不會在迴圈主體中改變：  
  
    ```  
    i = -100;  
    while( i < 0 ) {  
        i += x + y;  
    }  
    ```  
  
     經過最佳化後， `x + y`  只會計算一次而不是在每次迴圈執行時都要計算：  
  
    ```  
    i = -100;  
    t = x + y;  
    while( i < 0 ) {  
        i += t;  
    }  
    ```  
  
     如果編譯器可以假設沒有別名 \(以 [\_\_restrict](../../cpp/extension-restrict.md)、[noalias](../../cpp/noalias.md) 或 [restrict](../../cpp/restrict.md) 進行設定\)，則迴圈最佳化顯然會比較有效。  
  
    > [!NOTE]
    >  您可以使用 `optimize`  Pragma 配合 `g` 選項對每個函式逐一啟用或停用全域最佳化。  
  
 **\/Og** 也會啟用「指名傳回值」最佳化，以排除堆疊式傳回值的複製建構函式和解構函式。  如需詳細資訊，請參閱[\/O1、\/O2 \(最小大小、最快速度\)](../../build/reference/o1-o2-minimize-size-maximize-speed.md)。  
  
 如需相關資訊，請參閱[產生內建函式 \(\/Oi\)](../../build/reference/oi-generate-intrinsic-functions.md) 和[完全最佳化 \(\/Ox\)](../../build/reference/ox-full-optimization.md)。  
  
 **\/Og**已被取代；請使用 [\/O1](../../build/reference/o1-o2-minimize-size-maximize-speed.md) 或 **\/O2**。  如需詳細資訊，請參閱[Deprecated Compiler Options in Visual C\+\+ 2005](http://msdn.microsoft.com/zh-tw/aa59fce3-50b8-4f66-9aeb-ce09a7a84cce)。  
  
### 在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 \[**屬性頁**\] 對話方塊。  如需詳細資訊，請參閱 [如何：開啟專案屬性頁](../../misc/how-to-open-project-property-pages.md)。  
  
2.  按一下 \[**C\/C\+\+**\] 資料夾。  
  
3.  按一下 \[**命令列**\] 屬性頁。  
  
4.  在 \[**其他選項**\] 方塊中，輸入編譯器選項。  
  
### 若要以程式方式設定這個編譯器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。  
  
## 請參閱  
 [\/O 選項 \(最佳化程式碼\)](../../build/reference/o-options-optimize-code.md)   
 [編譯器選項](../../build/reference/compiler-options.md)   
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)