---
title: "嚴重錯誤 C1005 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C1005
dev_langs:
- C++
helpviewer_keywords:
- C1005
ms.assetid: 150daf8e-a38a-4669-9c1a-a05b5a1f65ef
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: e558112619e5cbefd641e7906df941d0869ceddb
ms.contentlocale: zh-tw
ms.lasthandoff: 10/10/2017

---
# <a name="fatal-error-c1005"></a>嚴重錯誤 C1005
字串太大超過緩衝區  
  
 編譯器中繼檔案中的字串造成緩衝區溢位。  
  
 當您傳遞至 [/Fd](../../build/reference/fd-program-database-file-name.md) 或 [/Yl](../../build/reference/yl-inject-pch-reference-for-debug-library.md) 編譯器選項的參數大於 256 個位元組時，可能會取得這項錯誤。
