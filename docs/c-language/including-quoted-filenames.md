---
title: "包含加引號的檔案名稱 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 789a047e-ea38-4c99-b71d-a2ad9c81daee
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 17c40e74a31341fc3a725c5e5b3823058e403cff
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="including-quoted-filenames"></a>包含加引號的檔案名稱
**ANSI 3.8.2**：針對可包含原始程式檔的加引號名稱支援  
  
 如果您以兩組雙引號 (" ") 指定 Include 檔完整明確的路徑規格，前置處理器只會搜尋該路徑規格並忽略標準目錄。  
  
 針對指定為 [#include](../preprocessor/hash-include-directive-c-cpp.md) "path-spec" 的 Include 檔案，目錄搜尋會先從父檔案的目錄開始，並繼續搜尋任何父父代檔案的目錄。 因此，搜尋會從包含處理中原始程式檔的目錄相對位置開始進行。 如果沒有上二層檔案，也找不到此檔案，則會繼續搜尋，如同以角括弧括住檔案名稱一般。  
  
## <a name="see-also"></a>另請參閱  
 [前置處理指示詞](../c-language/preprocessing-directives.md)