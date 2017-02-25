---
title: "/IMPLIB (名稱匯入程式庫) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/implib"
  - "VC.Project.VCLinkerTool.ImportLIbrary"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/IMPLIB 連結器選項"
  - "IMPLIB 連結器選項"
  - "-IMPLIB 連結器選項"
  - "匯入程式庫, 覆寫預設名稱"
ms.assetid: fe8f71ab-7055-41b5-8ef8-2b97cfa4a432
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# /IMPLIB (名稱匯入程式庫)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/IMPLIB:filename  
```  
  
## 備註  
 其中：  
  
 *filename*  
 是匯入程式庫的使用者定義名稱。  它會取代預設的名稱。  
  
## 備註  
 \/IMPLIB 選項會覆寫當 LINK 在建置含有匯出的程式時所建立之匯入程式庫的預設名稱。  預設名稱是由主要輸出檔的主檔名及副檔名 .lib 所組成。  如果指定了以下一種或多種情況，程式便含有匯出：  
  
-   原始程式碼中的 [\_\_declspec\(dllexport\)](../../cpp/dllexport-dllimport.md) 關鍵字  
  
-   在 .def 檔中的 [EXPORTS](../../build/reference/exports.md) 陳述式  
  
-   LINK 命令中的 [\/EXPORT](../../build/reference/export-exports-a-function.md) 規格  
  
 如果並未建立匯入程式庫，LINK 便會忽略 \/IMPLIB。  如果沒有指定匯出，LINK 將不會建立匯入程式庫。  如果在組建中使用了匯出檔，LINK 會假設匯入程式庫已經存在並且不會再建立匯入程式庫。  如需有關匯入程式庫和匯出檔的詳細資訊，請參閱 [LIB 參考](../../build/reference/lib-reference.md)。  
  
### 若要在 Visual Studio 開發環境中設定這個連結器選項  
  
1.  開啟專案的 \[**屬性頁**\] 對話方塊。  如需詳細資訊，請參閱[設定 Visual C\+\+ 專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  按一下 \[連結器\] 資料夾。  
  
3.  按一下 \[進階\] 屬性頁。  
  
4.  修改 \[匯入程式庫\] 屬性。  
  
### 若要以程式設計方式設定這個連結器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.ImportLibrary%2A>。  
  
## 請參閱  
 [設定連結器選項](../../build/reference/setting-linker-options.md)   
 [連結器選項](../../build/reference/linker-options.md)