---
title: 運算式評估工具錯誤 CXX0033
ms.date: 11/04/2016
f1_keywords:
- CXX0033
helpviewer_keywords:
- CAN0033
- CXX0033
ms.assetid: 0bd62c5b-de89-481f-9b12-88fe84805afe
ms.openlocfilehash: 8563eb2fbc24c6ad8db639d2e227802412a16090
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62397051"
---
# <a name="expression-evaluator-error-cxx0033"></a>運算式評估工具錯誤 CXX0033

OMF 型別資訊中的錯誤

可執行檔沒有有效的物件模組格式 (OMF) 進行偵錯。

此錯誤是與 can0033 相同。

### <a name="to-fix-by-checking-the-following-possible-causes"></a>透過檢查下列可能原因進行修正

1. 可執行檔不以發行使用此版本的視覺效果連結器建立C++。 重新連結物件程式碼使用 LINK.exe 的目前版本。

1. .Exe 檔案可能已損毀。 重新編譯並重新連結程式。