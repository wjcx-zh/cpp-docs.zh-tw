---
title: 特性指引最佳化錯誤 PG0165 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- PG0165
dev_langs:
- C++
helpviewer_keywords:
- PG0165
ms.assetid: e98122e7-ddee-4a2c-96b2-d232e4c65f3e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: acad97411480112d06dadd454d1368dcfdf2c87f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33318411"
---
# <a name="profile-guided-optimization-error-pg0165"></a>特性指引最佳化錯誤 PG0165
讀取 'Filename.pgd': ' 不支援的 PGD 版本 （版本不相符） '。  
  
 PGD 檔案是針對特定編譯器工具組。 當您使用比用於不同的編譯器會產生這個錯誤*Filename*.pgd。 此錯誤表示此編譯器工具組不能使用的資料從*Filename*.pgd 最佳化目前的處理序。  
  
 若要解決這個問題，重新產生*Filename*.pgd 使用目前的編譯器工具組。