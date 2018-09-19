---
title: 運算式評估工具錯誤 CXX0033 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- CXX0033
dev_langs:
- C++
helpviewer_keywords:
- CAN0033
- CXX0033
ms.assetid: 0bd62c5b-de89-481f-9b12-88fe84805afe
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 04f37b53c30d36a43d339132bfd9baca3e5ec70c
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46057193"
---
# <a name="expression-evaluator-error-cxx0033"></a>運算式評估工具錯誤 CXX0033

OMF 型別資訊中的錯誤

可執行檔沒有有效的物件模組格式 (OMF) 進行偵錯。

此錯誤是與 can0033 相同。

### <a name="to-fix-by-checking-the-following-possible-causes"></a>透過檢查下列可能原因進行修正

1. 不使用發行使用此版本的 Visual c + + 連結器建立可執行檔。 重新連結物件程式碼使用 LINK.exe 的目前版本。

1. .Exe 檔案可能已損毀。 重新編譯並重新連結程式。