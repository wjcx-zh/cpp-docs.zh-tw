---
title: 運算式評估工具錯誤 CXX0033
ms.date: 11/04/2016
f1_keywords:
- CXX0033
helpviewer_keywords:
- CAN0033
- CXX0033
ms.assetid: 0bd62c5b-de89-481f-9b12-88fe84805afe
ms.openlocfilehash: 2916808d98f1fabc2157fbedc96d76e196661279
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80195509"
---
# <a name="expression-evaluator-error-cxx0033"></a>運算式評估工具錯誤 CXX0033

OMF 類型資訊時發生錯誤

可執行檔沒有用來進行偵錯工具的有效物件模組格式（OMF）。

此錯誤與 CAN0033 相同。

### <a name="to-fix-by-checking-the-following-possible-causes"></a>透過檢查下列可能原因進行修正

1. 無法使用與此版本的 Visual C++一起發行的連結器來建立可執行檔。 使用目前的連結版本重新連結化物件程式碼。

1. .Exe 檔案可能已損毀。 重新編譯並重新連結程式。
