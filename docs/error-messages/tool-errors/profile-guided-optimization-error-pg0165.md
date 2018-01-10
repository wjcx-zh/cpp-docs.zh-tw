---
title: "特性指引最佳化錯誤 PG0165 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: PG0165
dev_langs: C++
helpviewer_keywords: PG0165
ms.assetid: e98122e7-ddee-4a2c-96b2-d232e4c65f3e
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 32b9f5f3ee335aac0a8382377aa850c3b91a27a0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="profile-guided-optimization-error-pg0165"></a>特性指引最佳化錯誤 PG0165
讀取 'Filename.pgd': ' 不支援的 PGD 版本 （版本不相符） '。  
  
 PGD 檔案是針對特定編譯器工具組。 當您使用比用於不同的編譯器會產生這個錯誤*Filename*.pgd。 此錯誤表示此編譯器工具組不能使用的資料從*Filename*.pgd 最佳化目前的處理序。  
  
 若要解決這個問題，重新產生*Filename*.pgd 使用目前的編譯器工具組。