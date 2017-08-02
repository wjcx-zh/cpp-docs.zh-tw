---
title: "配置零記憶體 | Microsoft Docs"
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
- memory allocation, zero memory
- zero memory
ms.assetid: 768f2ab9-83a1-4887-8eb5-c094c18489a8
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
ms.openlocfilehash: 05d05cefb6b35d4272c0e0e6fee29205de063fd4
ms.contentlocale: zh-tw
ms.lasthandoff: 05/18/2017

---
# <a name="allocating-zero-memory"></a>配置零記憶體
**ANSI 4.10.3** `calloc`、`malloc` 或 `realloc` 函式在所要求的大小為零時的行為  
  
 `calloc`、`malloc` 和 `realloc` 函式接受零做為引數。 其中未實際配置記憶體，不過會傳回有效的指標，而且稍後可以藉由 realloc 修改記憶體區塊。  
  
## <a name="see-also"></a>另請參閱  
 [程式庫函式](../c-language/library-functions.md)
