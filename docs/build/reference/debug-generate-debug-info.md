---
title: "/DEBUG (產生偵錯資訊) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCLinkerTool.GenerateDebugInformation"
  - "/debug"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - ".pdb 檔案, 產生偵錯資訊"
  - "/DEBUG 連結器選項"
  - "DEBUG 連結器選項"
  - "-DEBUG 連結器選項"
  - "偵錯 [C++], 偵錯資訊檔案"
  - "偵錯 [C++], 連結器選項"
  - "產生偵錯資訊連結器選項"
  - "PDB 檔案"
  - "pdb 檔案, 產生偵錯資訊"
  - "程式資料庫 [C++]"
ms.assetid: 1af389ae-3f8b-4d76-a087-1cdf861e9103
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# /DEBUG (產生偵錯資訊)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/DEBUG  
```  
  
## 備註  
 \/DEBUG 選項會建立 .exe 檔或 DLL 的偵錯資訊。  
  
 連結器會將偵錯資訊置入程式資料庫 \(PDB\) 中，  也會在後續的程式組建中更新這個 PDB。  
  
 為偵錯建立的 .exe 檔或 DLL 含有對應的 PDB 之名稱和路徑。  當您偵錯程式時，偵錯工具會讀取內嵌的名稱並且使用這個 PDB。  連結器會使用程式的主檔名和副檔名 .pdb 以命名程式資料庫，並且內嵌建立它的路徑。  若要覆寫這項預設，請設定 [\/PDB](../../build/reference/pdb-use-program-database.md) 並指定一個不同的名稱。  
  
 編譯器的[僅行數](../../build/reference/z7-zi-zi-debug-information-format.md) \(\/Zd\) 或 [C7 相容](../../build/reference/z7-zi-zi-debug-information-format.md) \(\/Z7\) 選項會使編譯器將偵錯資訊保留在 .obj 檔中。  您也可以使用[程式資料庫](../../build/reference/z7-zi-zi-debug-information-format.md) \(\/Zi\) 編譯器選項將偵錯資訊儲存在 .obj 檔的 PDB 中。  連結器會首先以 .obj 檔中所寫的絕對路徑尋找目的檔的 PDB，然後再搜尋含有該 .obj 檔的目錄。  您不能對連結器指定目的檔的 PDB 檔名或位置。  
  
 當指定 \/DEBUG 時，[\/INCREMENTAL](../../build/reference/incremental-link-incrementally.md) 亦隱含其中。  
  
 \/DEBUG 會將 [\/OPT](../../build/reference/opt-optimizations.md) 選項的預設值從 REF 變更為 NOREF，並從 ICF 變更為 NOICF \(因此，您必須明確地指定 \/OPT:REF 或 \/OPT:ICF\)。  
  
 如需有關 .PDB 和 .DBG 檔的詳細資訊，請參閱知識庫文件 Q121366＜INFO: PDB and DBG Files \- What They Are and How They Work＞。  您可以在 MSDN 文件庫或是在 [http:\/\/search.support.microsoft.com](http://support.microsoft.com/) 找到知識庫文件。  
  
 您不可能建立包含偵錯資訊的 .exe 或 .dll。  偵錯資訊一定都會放置於 .pdb 檔中。  
  
### 若要在 Visual Studio 開發環境中設定這個連結器選項  
  
1.  開啟專案的 \[**屬性頁**\] 對話方塊。  如需詳細資訊，請參閱[設定 Visual C\+\+ 專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  按一下 \[連結器\] 資料夾。  
  
3.  按一下 \[**偵錯**\] 屬性頁。  
  
4.  修改 \[產生偵錯資訊\] 屬性。  
  
### 若要以程式設計方式設定這個連結器選項  
  
1.  請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.GenerateDebugInformation%2A>。  
  
## 請參閱  
 [設定連結器選項](../../build/reference/setting-linker-options.md)   
 [連結器選項](../../build/reference/linker-options.md)