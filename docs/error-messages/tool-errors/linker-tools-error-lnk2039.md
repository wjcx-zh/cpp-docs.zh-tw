---
title: "連結器工具錯誤 LNK2039 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- LNK2039
dev_langs:
- C++
helpviewer_keywords:
- LNK2039
ms.assetid: eaa296bd-4901-41f6-8410-6d03ee827144
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 441765d85ce65a80102ed94b3f4394ae48c0e29f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-error-lnk2039"></a>連結器工具錯誤 LNK2039
匯入的 ref 類別\<類型 >'，它定義於.obj; 它應該是其中一種匯入或定義，但非兩者皆是  
  
 Ref 類別 ' <`type`>' 匯入指定的.obj 檔案，但也會定義在另一個.obj 檔案。 這種情況可能會造成執行階段錯誤或其他未預期的行為。  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
1.  檢查 '`type`' 是否必須定義於另一個 .obj 檔案，並檢查是否必須從 .winmd 檔案匯入它。  
  
2.  移除定義或匯入。  
  
## <a name="see-also"></a>請參閱  
 [連結器工具錯誤和警告](../../error-messages/tool-errors/linker-tools-errors-and-warnings.md)   
 [連結器工具錯誤 LNK1332](../../error-messages/tool-errors/linker-tools-error-lnk1332.md)