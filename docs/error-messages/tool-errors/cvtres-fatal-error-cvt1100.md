---
title: CVTRES 嚴重錯誤 CVT1100
ms.date: 11/04/2016
f1_keywords:
- CVT1100
helpviewer_keywords:
- CVT1100
ms.assetid: 886e88dd-5818-4b5f-84f2-d2a3d75f0aaf
ms.openlocfilehash: b7e67df24d41b1e8826673146fcc27fd93d143fd
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80196543"
---
# <a name="cvtres-fatal-error-cvt1100"></a>CVTRES 嚴重錯誤 CVT1100

重複的資源—類型：類型，名稱：名稱，語言：語言，旗標：旗標，大小：大小

指定的資源超過一次以上。

如果連結器正在建立型別程式庫，而您未指定[/TLBID](../../build/reference/tlbid-specify-resource-id-for-typelib.md) ，而且專案中的資源已經使用1，您就會收到這個錯誤。 在此情況下，請指定/TLBID，並指定最多65535的另一個數位。
