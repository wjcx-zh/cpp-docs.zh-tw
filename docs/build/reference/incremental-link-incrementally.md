---
title: "/INCREMENTAL (以累加方式連結) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/incremental"
  - "VC.Project.VCLinkerTool.LinkIncremental"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/INCREMENTAL 連結器選項"
  - "INCREMENTAL 連結器選項"
  - "-INCREMENTAL 連結器選項"
  - "累加連結"
  - "累加連結選項"
  - "LINK 工具 [C++], 完全連結的選項"
ms.assetid: 135656ff-94fa-4ad4-a613-22e1a2a5d16b
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# /INCREMENTAL (以累加方式連結)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/INCREMENTAL[:NO]  
```  
  
## 備註  
 控制連結器處理累加連結的方式。  
  
 根據預設，連結器是以累加模式執行。  若要覆寫預設的累加連結，請指定 \/INCREMENTAL:NO。  
  
 以累加方式連結的程式和以非累加方式連結的程式在功能方面不相上下。  但是，由於要為後續累加連結作準備，因此以累加方式連結的可執行檔 \(.exe\) 或動態連結程式庫 \(DLL\)：  
  
-   因為程式碼和資料的填補，會比以非累加方式連結的程式大一些 \(填補可以讓連結器增加函式和資料的大小，而不需重新建立 .exe 檔\)。  
  
-   可能包含跳躍點 \(Jump\) Thunk，用以將函式重新配置到新的位址。  
  
    > [!NOTE]
    >  若要確保您的最終版本組建不包含填補或 Thunk，請以非累加方式連結您的程式。  
  
 若要在不考慮預設值的情況下以累加方式連結，請指定 \/INCREMENTAL。  選取這個選項時，如果無法以累加方式連結，連結器便會發出警告，然後以非累加方式連結程式。  有些選項和情況會覆寫 \/INCREMENTAL。  
  
 大部分程式都可以用累加方式連結。  然而，有些變更可能太大，而且有些選項與累加連結不相容。  如果指定了以下任何選項，LINK 便會執行完整連結：  
  
-   未選取以累加方式連結 \(\/INCREMENTAL:NO\)  
  
-   選取 \/OPT:REF  
  
-   選取 \/OPT:ICF  
  
-   選取 \/OPT:LBR  
  
-   選取 \/ORDER  
  
 當指定 [\/DEBUG](../../build/reference/debug-generate-debug-info.md) 時，隱含了 \/INCREMENTAL。  
  
 此外，如果發生下列任何情況，LINK 也會執行完整連結：  
  
-   找不到累加狀態檔 \(.ilk\) \(LINK 會為後續的累加連結建立新的 .ilk 檔\)。  
  
-   對 .ilk 檔沒有寫入權限 \(LINK 會忽略 .ilk 檔並且以非累加方式連結\)。  
  
-   找不到 .exe 或 .dll 輸出檔。  
  
-   .ilk、.exe 或 .dll 的時間戳記已變更。  
  
-   某個 LINK 選項已變更。  大部分 LINK 選項在不同組建之間有所變更時，都會產生完整連結。  
  
-   加入或省略了某個目的檔 \(.obj\)。  
  
### 在 Visual Studio 開發環境中設定這個連結器選項  
  
1.  開啟專案的 \[**屬性頁**\] 對話方塊。  如需詳細資訊，請參閱 [使用專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  選取 \[**連結器**\] 資料夾。  
  
3.  選取 \[**一般**\] 屬性頁。  
  
4.  修改 \[**啟用累加連結**\] 屬性。  
  
### 若要以程式設計方式設定這個連結器選項  
  
1.  請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.LinkIncremental%2A>。  
  
## 請參閱  
 [設定連結器選項](../../build/reference/setting-linker-options.md)   
 [連結器選項](../../build/reference/linker-options.md)