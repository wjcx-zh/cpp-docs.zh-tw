---
title: "使用匯入程式庫和匯出檔案 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "循環匯出"
  - "匯出檔案"
  - "匯入程式庫, 使用"
ms.assetid: 2634256a-8aa5-4495-8c9e-6cde10e4ed76
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 使用匯入程式庫和匯出檔案
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

當程式 \(可執行檔或 DLL\) 匯出到也是它匯入來源的另一個程式時，或者如果有兩個以上的程式同時匯出和匯入到彼此之間，連結這些程式的命令必須允許循環匯出。  
  
 在沒有循環匯出的情形下，當連結一個使用其他程式之匯出的程式時，您必須為匯出程式指定匯入程式庫。  當您連結匯出程式時，即建立了匯出程式的匯入程式庫。  因此，您必須在匯入程式前連結匯出程式。  例如，如果 TWO.dll 要從 ONE.dll 匯入，您必須先連結 ONE.dll，然後取得匯入程式庫 ONE.lib。  接著，在連結 TWO.dll 時指定 ONE.lib。  當連結器建立 TWO.dll 時，同時也會建立它的匯入程式庫 TWO.lib。  當連結從 TWO.dll 匯入的程式時，便可使用 TWO.lib。  
  
 然而，在循環匯出的情形下，不可能從其他程式使用匯入程式庫連結所有的互相依存程式。  在先前所討論的範例中，如果 TWO.dll 也匯出到 ONE.dll，則當連結 ONE.dll 時，TWO.dll 的匯入程式庫還尚未存在。  當循環匯出存在時，您必須使用 LIB 為這些程式之一來建立匯入程式庫和匯出檔案。  
  
 首先，選擇其中一個程式來執行 LIB。  在 LIB 命令中，列出程式所有的物件和程式庫，並指定 \/DEF。  如果程式有使用 .def 檔案或 \/EXPORT 規格，也請同時指定。  
  
 在您為程式建立匯入程式庫 \(.lib\) 和匯出檔案 \(.exp\) 後，您便可以在連結其他的檔案時，使用匯入程式庫。  LINK 會為它所建置的每一個匯出程式建立匯入程式庫。  例如，如果您針對 ONE.dll 在物件和匯出上執行 LIB，您即建立了 ONE.lib 和 ONE.exp。  您現在可以在連結 TWO.dll 時使用 ONE.lib；而這個步驟也建立了匯入程式庫 TWO.lib。  
  
 最後，連結您啟始的程式。  在 LINK 命令中，指定程式的物件和程式庫、LIB 為程式所建立的 .exp 檔案和程式使用的匯出之匯入程式庫。  若要繼續這個範例，ONE.dll 的 LINK 命令會包含 ONE.exp 和 TWO.lib，以及進入 ONE.dll 的物件和程式庫。  不要在 LINK 命令指定 .def 檔案或 \/EXPORT 規格；這些是不需要的，因為匯出定義包含在 .exp 檔案裡。  因為 Link 假設在 .exp 檔案建立時已建立了匯入程式庫，因此當您使用 .exp 檔案連結時，不會建立匯入程式庫。  
  
## 請參閱  
 [與匯入程式庫和匯出檔案一起使用](../../build/reference/working-with-import-libraries-and-export-files.md)