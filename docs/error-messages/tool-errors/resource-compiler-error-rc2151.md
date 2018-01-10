---
title: "資源編譯器錯誤 RC2151 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: RC2151
dev_langs: C++
helpviewer_keywords: RC2151
ms.assetid: 3c47e535-c78d-4338-aab9-9b47e2c34728
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: beabd61c64c296bf454aa94b8f915673b5f0cfca
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="resource-compiler-error-rc2151"></a>資源編譯器錯誤 RC2151
無法重新使用字串常數  
  
 您要使用相同的值在兩次**STRINGTABLE**陳述式。 請確定您未混淆重疊的十進位和十六進位值。  
  
 在每個識別碼**STRINGTABLE**必須是唯一的。 最大效率使用連續的常數，以開始 16 的倍數。