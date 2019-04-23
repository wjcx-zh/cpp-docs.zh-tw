---
title: 編譯器錯誤 C3888
ms.date: 11/04/2016
f1_keywords:
- C3888
helpviewer_keywords:
- C3888
ms.assetid: 40820812-79c5-4dcd-a19d-b4164d25fc8a
ms.openlocfilehash: e4d52946126e7be6c6f2aef34b5eb5a93a0babad
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59033637"
---
# <a name="compiler-error-c3888"></a>編譯器錯誤 C3888

'name' : C++/CLI 不支援與這個常值資料成員關聯的常數運算式

使用 *常值* 關鍵字所宣告的 [名稱](../../extensions/literal-cpp-component-extensions.md) 資料成員，是以編譯器不支援的值進行初始化。 編譯器僅支援常數整數、列舉或字串類型。 **C3888** 錯誤的可能原因是資料成員使用位元組陣列進行初始化。

### <a name="to-correct-this-error"></a>更正這個錯誤

1. 請檢查宣告的常值資料成員是支援的類型。

## <a name="see-also"></a>另請參閱

[名稱](../../extensions/literal-cpp-component-extensions.md)