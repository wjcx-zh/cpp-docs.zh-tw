---
title: "/EXPORT (匯出函式) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCLinkerTool.ExportFunctions"
  - "/export"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/EXPORT 連結器選項"
  - "EXPORT 連結器選項"
  - "-EXPORT 連結器選項"
ms.assetid: 0920fb44-a472-4091-a8e6-73051f494ca0
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# /EXPORT (匯出函式)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/EXPORT:entryname[,@ordinal[,NONAME]][,DATA]  
```  
  
## 備註  
 使用這個選項，您可以從您的程式匯出一個函式，讓其他程式能夠呼叫它。  您也可以匯出資料。  匯出通常定義於 DLL 中。  
  
 當呼叫的程式使用 *entryname* 時，它是函式或資料項目的名稱。  `ordinal` 會指定一個範圍在 1 到 65,535 之間的匯出表格索引；如果您不指定 `ordinal`，LINK 會指派一個。  **NONAME** 關鍵字只以序數匯出函式，沒有 *entryname*。  
  
 **DATA** 關鍵字是表示匯出的項目為資料項目。  用戶端程式中的資料項目必須用 **extern \_\_declspec\(dllimport\)** 宣告。  
  
 以下是三種匯出定義的方法，以建議使用的順序列出：  
  
1.  在原始程式碼中的 [\_\_declspec\(dllexport\)](../../cpp/dllexport-dllimport.md)  
  
2.  .def 檔中的 [EXPORTS](../../build/reference/exports.md) 陳述式  
  
3.  在 LINK 命令中的 \/EXPORT 規格  
  
 您可在同一個程式中使用這全部三種方法。  當 LINK 建置包含匯出的程式時，除非建置中使用 .exp 檔，否則它也會建立一個匯入程式庫。  
  
 LINK 會使用識別項的裝飾形式。  編譯器會在建立 .obj 檔時裝飾識別項。  如果 *entryname* 是以未裝飾的形式 \(像它出現在原始程式碼中時一樣\) 指定給連結器，LINK 會嘗試去比對名稱。  如果找不到唯一的符合項目，LINK 便會發出錯誤訊息。  當您需要指定識別項給連結器時，請使用 [DUMPBIN](../../build/reference/dumpbin-reference.md) 工具取得識別項[裝飾名稱](../../build/reference/decorated-names.md)的形式。  
  
> [!NOTE]
>  不要指定已宣告為 `__cdecl` 或 `__stdcall` 之 C 識別項的裝飾形式。  
  
### 若要在 Visual Studio 開發環境中設定這個連結器選項  
  
1.  開啟專案的 \[**屬性頁**\] 對話方塊。  如需詳細資訊，請參閱[設定 Visual C\+\+ 專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  按一下 \[連結器\] 資料夾。  
  
3.  按一下 \[**命令列**\] 屬性頁。  
  
4.  在 \[**其他選項**\] 方塊中輸入選項。  
  
### 若要以程式設計方式設定這個連結器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>。  
  
## 請參閱  
 [設定連結器選項](../../build/reference/setting-linker-options.md)   
 [連結器選項](../../build/reference/linker-options.md)