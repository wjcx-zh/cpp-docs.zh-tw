---
title: CVTRES 嚴重錯誤 CVT1100
ms.date: 11/04/2016
f1_keywords:
- CVT1100
helpviewer_keywords:
- CVT1100
ms.assetid: 886e88dd-5818-4b5f-84f2-d2a3d75f0aaf
ms.openlocfilehash: c7e65ccc79852ec99dd2406398fe1b3cdecacde7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50429298"
---
# <a name="cvtres-fatal-error-cvt1100"></a>CVTRES 嚴重錯誤 CVT1100

重複的資源-類型： 類型、 名稱： 名稱、 語言:、 旗標： 旗標、 大小： 大小

指定的資源已指定一次以上。

您可以取得此錯誤，如果連結器會建立型別程式庫，而且您未指定[/TLBID](../../build/reference/tlbid-specify-resource-id-for-typelib.md)和您的專案中的資源已使用 1。 在此情況下，指定 /TLBID，並指定另一個數字，最多 65535。