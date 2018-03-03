---
title: "建立匯入程式庫和匯出檔案 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCLibrarianTool.ModuleDefinitionFile
- VC.Project.VCLibrarianTool.ExportNamedFunctions
- VC.Project.VCLibrarianTool.GenerateDebug
- VC.Project.VCLibrarianTool.ForceSymbolReferences
dev_langs:
- C++
helpviewer_keywords:
- OUT library manager option
- INCLUDE library manager option
- /DEF library manager option
- exporting data
- import libraries, building
- -INCLUDE library manager option
- /OUT library manager option
- DEF library manager option
- -DEF library manager option
- -OUT library manager option
- /INCLUDE library manager option
- -EXPORT library manager option
- exporting data, export (.exp) files
- /EXPORT library manager option
- EXPORT library manager option
- .lib files
- EXP files
ms.assetid: 2fe4f30a-1dd6-4b05-84b5-0752e1dee354
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 979e052147f058e6c46a1c10b1dd89cfd36ee362
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="building-an-import-library-and-export-file"></a>建置匯入程式庫和匯出檔案
若要建置之匯入程式庫和匯出檔案，使用下列語法：  
  
```  
LIB /DEF[:deffile] [options] [objfiles] [libraries]  
```  
  
 /DEF 指定時，LIB 所建立的輸出檔案從匯出規格的傳入 LIB 命令。 有三種方法，可指定匯出，建議使用的順序中所列：  
  
1.  A **__declspec （dllexport)**其中一種定義*objfiles*或*程式庫*  
  
2.  /EXPORT 規格：*名稱*LIB 命令列上  
  
3.  中的定義**匯出**中的陳述式`deffile`  
  
 這些是您用來連結匯出的程式時，指定匯出的相同方法。 程式可以使用一個以上的方法。 您可以指定組件的 LIB 命令 (例如多個*objfiles*或 /EXPORT 規格) LIB 命令中的命令檔，就像您可以在 LINK 命令中。  
  
 下列選項會套用至建置匯入程式庫和匯出檔案：  
  
 / 輸入輸出：*匯入*  
 覆寫預設的輸出檔案名稱，如*匯入*正在建立的程式庫。 若未指定 /OUT，預設名稱是基底名稱的第一個目的檔或程式庫中的 LIB 命令和延伸模組。 lib。 匯出檔案會採用相同的基底名稱為匯入程式庫和擴充。 exp。  
  
 / 匯出： *entryname*[= *internalname*] [，@ `ordinal`[， **NONAME**]] [，**資料**]  
 匯出函式，從您的程式，以允許其他程式來呼叫此函式。 您也可以匯出資料 (使用**資料**關鍵字)。 匯出通常被定義在 DLL 中。  
  
 *Entryname*是函式或資料的項目名稱，因為它是可供呼叫端程式。 您可以選擇性地指定*internalname*當做函式定義的程式中; 依預設，已知*internalname*相同*entryname*。 `ordinal`指定範圍 1 到 65535 之間的匯出資料表的索引，如果您未指定`ordinal`，LIB 指派其中一個。 **NONAME**關鍵字匯出函式只能做為序數，而不*entryname*。 **資料**關鍵字用來匯出只有資料的物件。  
  
 / 包括：`symbol`  
 將指定的符號加入至符號表。 此選項可用於強制執行的程式庫物件，否則不會包含使用。  
  
 請注意，是否您在預備步驟中，建立您匯入程式庫建立.dll 之前時，您必須傳遞相同的物件檔案集建置.dll 時為您成功建置匯入程式庫時。  
  
## <a name="see-also"></a>請參閱  
 [與匯入程式庫和匯出檔案一起使用](../../build/reference/working-with-import-libraries-and-export-files.md)