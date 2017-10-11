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
ms.translationtype: HT
ms.sourcegitcommit: 16d1bf59dfd4b3ef5f037aed9c0f6febfdf1a2e8
ms.openlocfilehash: ebbb6ab903db73fce84059af567dd5e80dfb3afb
ms.contentlocale: zh-tw
ms.lasthandoff: 10/09/2017

---
# <a name="file-position-errors"></a>檔案位置錯誤
**ANSI 4.9.9.1, 4.9.9.4**：失敗時，`fgetpos` 或 `ftell` 函式要將巨集 `errno` 設定成的值  
  
 當 `fgetpos` 或 `ftell` 失敗時，如果位置無效，會將 `errno` 設定為資訊清單常數 `EINVAL`，如果檔案編號錯誤則會設為 EBADF。 這些常數都在 ERRNO.H 中定義。  
  
## <a name="see-also"></a>另請參閱  
 [程式庫函式](../c-language/library-functions.md)
