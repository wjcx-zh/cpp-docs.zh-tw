---
title: "/MAP (產生對應檔) | Microsoft Docs"
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
  - "/map"
  - "VC.Project.VCLinkerTool.MapFileName"
  - "VC.Project.VCLinkerTool.GenerateMapFile"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/MAP 連結器選項"
  - "產生對應檔連結器選項"
  - "MAP 連結器選項"
  - "-MAP 連結器選項"
  - "mapfile 連結器選項"
  - "對應檔, 建立連結器"
  - "對應檔, 連結程式的相關資訊"
  - "對應檔, 指定檔案名稱"
ms.assetid: 9ccce53d-4e36-43da-87b0-7603ddfdea63
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /MAP (產生對應檔)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/MAP[:filename]  
```  
  
## 備註  
 其中：  
  
 *filename*  
 使用者指定的對應檔名稱。  它會取代預設的名稱。  
  
## 備註  
 \/MAP 選項會告訴連結器建立一個對應檔。  
  
 依預設值，連結器會以程式的主檔名和副檔名 .map 來命名對應檔。  選擇性的 *filename* 可以讓您覆寫對應檔的預設名稱。  
  
 對應檔是個文字檔，含有所要連結程式的下列資訊：  
  
-   模組名稱，也是檔案的主檔名  
  
-   程式檔案標頭的 \(不是檔案系統的\) 時間戳記  
  
-   程式中群組的清單，並附有每一群組的開始位址 \(如 *section*:*offset*\)、長度、群組名稱和類別  
  
-   公用符號的清單，並附有符號被定義的每一位址 \(如 *section*:*offset*\)、符號名稱、Flat 位址和 .obj 檔  
  
-   進入點 \(如 *section*:*offset*\)  
  
 [\/MAPINFO](../../build/reference/mapinfo-include-information-in-mapfile.md) 選項是指定要包括在對應檔中的其他資訊。  
  
### 若要在 Visual Studio 開發環境中設定這個連結器選項  
  
1.  開啟專案的 \[**屬性頁**\] 對話方塊。  如需詳細資訊，請參閱[設定 Visual C\+\+ 專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  按一下 \[連結器\] 資料夾。  
  
3.  按一下 \[偵錯\] 屬性頁。  
  
4.  修改 \[產生對應檔\] 屬性。  
  
### 若要以程式設計方式設定這個連結器選項  
  
1.  請參閱<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.GenerateMapFile%2A>以及<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.MapFileName%2A>。  
  
## 請參閱  
 [設定連結器選項](../../build/reference/setting-linker-options.md)   
 [連結器選項](../../build/reference/linker-options.md)