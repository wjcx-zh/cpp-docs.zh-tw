---
title: 嚴重錯誤 C1005 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1005
dev_langs:
- C++
helpviewer_keywords:
- C1005
ms.assetid: 150daf8e-a38a-4669-9c1a-a05b5a1f65ef
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 13ff7f5dbc1f9ecb66c54f52fae4a38d1e4d4664
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33197711"
---
# <a name="fatal-error-c1005"></a>嚴重錯誤 C1005
字串太大超過緩衝區  
  
 編譯器中繼檔案中的字串造成緩衝區溢位。  
  
 當您傳遞至 [/Fd](../../build/reference/fd-program-database-file-name.md) 或 [/Yl](../../build/reference/yl-inject-pch-reference-for-debug-library.md) 編譯器選項的參數大於 256 個位元組時，可能會取得這項錯誤。