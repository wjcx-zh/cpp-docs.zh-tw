---
title: 區塊 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- function definitions, blocks in code
- blocks
- compound statements
- statements, compound
ms.assetid: be231a92-c712-464e-ae25-a4becb20f7f5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 309e6c017587a2dd3cdc80cd55ffec82751dedd3
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32380936"
---
# <a name="blocks"></a>區塊
在大括號 (**{ }**) 內的宣告、定義和陳述式序列稱為「區塊」。 C 中有兩種類型的區塊。其中一種類型的區塊為「複合陳述式」，是由一個或多個陳述式所組成的陳述式 (請參閱[複合陳述式](../c-language/compound-statement-c.md))。 另一種類型的區塊為「函式定義」，是由複合陳述式 (函式主體) 加上函式的關聯「標頭」(函式名稱、傳回型別及正式參數) 所組成。 位於區塊內的區塊稱為「巢狀」。  
  
 請注意，雖然所有複合陳述式都會以大括號括住，但是並非以大括號括住的所有項目都會構成複合陳述式。 例如，雖然陣列、結構或列舉元素的規格可以出現在大括號內，但它們不是複合陳述式。  
  
## <a name="see-also"></a>請參閱  
 [原始程式檔和來源程式](../c-language/source-files-and-source-programs.md)