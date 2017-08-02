---
title: "檔案位置錯誤 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- file pointers [C++], file position errors
ms.assetid: d5e59d8b-08c0-4927-a338-0b2d8234ce24
caps.latest.revision: 6
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: d6eb43b2e77b11f4c85f6cf7e563fe743d2a7093
ms.openlocfilehash: f81176b3b92b7ab92954947bb98e3bd14b93a290
ms.contentlocale: zh-tw
ms.lasthandoff: 05/18/2017

---
# <a name="file-position-errors"></a>檔案位置錯誤
**ANSI 4.9.9.1, 4.9.9.4**：失敗時，`fgetpos` 或 `ftell` 函式要將巨集 `errno` 設定成的值  
  
 當 `fgetpos` 或 `ftell` 失敗時，如果位置無效，會將 `errno` 設定為資訊清單常數 `EINVAL`，如果檔案編號錯誤則會設為 EBADF。 這些常數都在 ERRNO.H 中定義。  
  
## <a name="see-also"></a>另請參閱  
 [程式庫函式](../c-language/library-functions.md)
