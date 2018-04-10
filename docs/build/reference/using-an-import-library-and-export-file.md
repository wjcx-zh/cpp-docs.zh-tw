---
title: 使用匯入程式庫和匯出檔案 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-tools
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- circular exports
- import libraries, using
- export files
ms.assetid: 2634256a-8aa5-4495-8c9e-6cde10e4ed76
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 37d77fdc4df7d2e7239b8bba652d8cf8f4bbc997
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="using-an-import-library-and-export-file"></a>使用匯入程式庫和匯出檔案
當程式 （可執行檔或 DLL） 將匯出到另一個程式，它也會從匯入，或如果兩個以上的程式來匯出和匯入到彼此，來連結這些程式的命令必須配合循環匯出。  
  
 沒有循環匯出的情況下，當連結使用的程式，匯出從另一個程式，您必須指定匯出程式匯入程式庫。 連結匯出程式時，會建立匯出程式匯入程式庫。 因此，您必須連結之前匯入程式匯出的程式。 例如，如果 TWO.dll 匯入從 ONE.dll，您必須先將連結 ONE.dll 並取得匯入程式庫 ONE.lib。 然後，您指定 ONE.lib 連結 TWO.dll 時。 當連結器建立 TWO.dll 時，它也會建立其匯入程式庫，TWO.lib。 當連結從 TWO.dll 匯入的程式，請使用 TWO.lib。  
  
 不過，在循環匯出的情況下，不可能全部具有相依性的程式使用來自其他程式匯入程式庫連結。 在範例中討論的內容，如果 TWO.dll 也會匯出 ONE.dll、 TWO.dll 匯入程式庫不存在，但 ONE.dll 連結時。 循環匯出存在時，您必須使用 LIB 建立匯入程式庫和匯出檔案的其中一個程式。  
  
 若要開始，請選擇其中一個要執行 LIB 程式。 在 LIB 命令中，列出所有物件和程式的程式庫，並指定 /def。 如果程式使用.def 檔或 /EXPORT 規格，指定這些選項以及。  
  
 您建立匯入程式庫 (.lib) 和程式的匯出檔案 (.exp) 之後，您使用匯入程式庫，連結的其他程式時也一樣。 連結會建立每個匯出的程式，它會建置匯入程式庫。 例如，如果您執行 LIB 物件和匯出 ONE.dll，您建立 ONE.lib 和 ONE.exp。您現在可以在連結 TWO.dll; 時使用 ONE.lib這個步驟也會建立匯入程式庫 TWO.lib。  
  
 最後，將您開始使用程式的連結。 LINK 命令中，在指定的物件和程式、 程式庫建立程式，以及匯入程式庫的.exp 檔案的程式庫或文件庫的程式所使用的匯出。 若要繼續此範例，ONE.dll 連結命令包含 ONE.exp 和 TWO.lib，以及物件，以及移入 ONE.dll 文件庫。 未指定.def 檔或 /EXPORT 規格中連結的命令。不需要用到這些，因為匯出定義包含.exp 檔案中。 當您使用.exp 檔，連結並不會建立匯入程式庫，因為它會假設一個.exp 檔建立時建立。  
  
## <a name="see-also"></a>請參閱  
 [與匯入程式庫和匯出檔案一起使用](../../build/reference/working-with-import-libraries-and-export-files.md)