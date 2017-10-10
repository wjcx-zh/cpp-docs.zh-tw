---
title: "嚴重錯誤 C1033 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C1033
dev_langs:
- C++
helpviewer_keywords:
- C1033
ms.assetid: 09976c03-8450-4cf7-8b43-1b91c2c2b9f9
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: a0c9c67d23f2d0b957fb3e43844245029efedc64
ms.contentlocale: zh-tw
ms.lasthandoff: 10/10/2017

---
# <a name="fatal-error-c1033"></a>嚴重錯誤 C1033
無法開啟程式資料庫 pdb  
  
 這個錯誤可能被因磁碟錯誤。  
  
 在 Visual c + +.NET 2002 中，檔案名稱 （或檔案名稱的目錄路徑） 包含 MBCS 字元時，則必須正確設定使用者地區設定。 設定系統地區設定是不夠的；必須設定使用者地區設定，才能處理 MBCS 字元。  
  
 如需詳細資訊，請參閱[http://support.microsoft.com/default.aspx?scid=kb;en-us;246007](http://support.microsoft.com/default.aspx?scid=kb;en-us;246007)。
