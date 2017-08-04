---
title: "ANSI C 合規性 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- Ansi
dev_langs:
- C++
helpviewer_keywords:
- underscores, leading
- compatibility [C++], ANSI C
- compliance with ANSI C
- conventions [C++], Microsoft extensions
- underscores
- naming conventions [C++], Microsoft library
- ANSI [C++], C standard
- Microsoft extensions naming conventions
ms.assetid: 6be271bf-eecf-491a-a928-0ee2dd60e3b9
caps.latest.revision: 6
author: corob-msft
ms.author: corob
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
ms.openlocfilehash: 7e6c5d4045f0b71890a34d845b898844ca550ca8
ms.contentlocale: zh-tw
ms.lasthandoff: 05/18/2017

---
# <a name="ansi-c-compliance"></a>ANSI C 合規性
執行階段系統中所有 Microsoft 特定識別碼 (例如函式、巨集、常數、變數與類型定義) 的命名慣例都符合 ANSI 標準。 在此文件中，依照 ANSI/ISO C 標準的所有執行階段函式都標示為與 ANSI 相容。 符合 ANSI 標準的應用程式應該只使用這些與 ANSI 相容的函式。  
  
 Microsoft 特定函式與全域變數的開頭都是一個底線字元。 這些名稱只能在程式碼的範圍內以區域方式覆寫。 例如，當您包含 Microsoft 執行階段標頭檔時，仍然能透過宣告相同名稱的區域變數，以區域方式覆寫名為 `_open` 的 Microsoft 特定函式。 然而，您無法為自己的全域函式或全域變數使用此名稱。  
  
 Microsoft 特定巨集與資訊清單常數名稱的開頭是兩個底線字元，或是一個前置底線字元加上一個大寫字母。 這些識別碼的範圍是絕對範圍。 例如，您無法針對此理由使用 Microsoft 特定識別碼 **_UPPER**。  
  
## <a name="see-also"></a>另請參閱  
 [相容性](../c-runtime-library/compatibility.md)
