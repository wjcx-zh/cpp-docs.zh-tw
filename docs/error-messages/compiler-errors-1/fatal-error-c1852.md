---
title: 嚴重錯誤 C1852 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1852
dev_langs:
- C++
helpviewer_keywords:
- C1852
ms.assetid: fa011004-b8d6-46f1-ba80-4785e4ce137f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0adfa7eed25f1902300fa2378b8ffc19eb8dfafd
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46023796"
---
# <a name="fatal-error-c1852"></a>嚴重錯誤 C1852

'filename' 是無效的先行編譯標頭檔

檔案不是先行編譯標頭檔。

### <a name="to-fix-by-checking-the-following-possible-causes"></a>透過檢查下列可能原因進行修正

1. 使用 **/Yu** 或 **#pragma hdrstop**指定的檔案無效。

1. 如果您未指定副檔名，編譯器會假設副檔名為 .pch。