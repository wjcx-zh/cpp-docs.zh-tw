---
title: CVTRES 嚴重錯誤 CVT1100 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- CVT1100
dev_langs:
- C++
helpviewer_keywords:
- CVT1100
ms.assetid: 886e88dd-5818-4b5f-84f2-d2a3d75f0aaf
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 18a5508301c54637fb34a751c8f1c4e307e47d50
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46068958"
---
# <a name="cvtres-fatal-error-cvt1100"></a>CVTRES 嚴重錯誤 CVT1100

重複的資源-類型： 類型、 名稱： 名稱、 語言:、 旗標： 旗標、 大小： 大小

指定的資源已指定一次以上。

您可以取得此錯誤，如果連結器會建立型別程式庫，而且您未指定[/TLBID](../../build/reference/tlbid-specify-resource-id-for-typelib.md)和您的專案中的資源已使用 1。 在此情況下，指定 /TLBID，並指定另一個數字，最多 65535。