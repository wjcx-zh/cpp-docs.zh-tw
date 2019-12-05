---
title: 編譯器警告 (層級 1) C4910
ms.date: 11/04/2016
f1_keywords:
- C4910
helpviewer_keywords:
- C4910
ms.assetid: 67963560-fbca-4ca7-93db-06beaf7055f0
ms.openlocfilehash: a3f29cb895da8c06ed43dd5c9956426f3f6014f1
ms.sourcegitcommit: 8762a3f9b5476b4dee03f0ee8064ea606550986e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/04/2019
ms.locfileid: "74810711"
---
# <a name="compiler-warning-level-1-c4910"></a>編譯器警告 (層級 1) C4910

'\<識別碼 > '： ' __declspec （dllexport） ' 和 ' extern ' 在明確具現化上不相容

`__declspec(dllexport)` 和 `extern` 關鍵字會同時修改名為 *\<identifier >* 的明確樣板具現化。 不過，這些關鍵字是互斥的。 `__declspec(dllexport)` 關鍵字表示具現化樣板類別，而 `extern` 關鍵字表示不會自動具現化樣板類別。

## <a name="see-also"></a>請參閱

[明確初始化](../../cpp/explicit-instantiation.md)<br/>
[dllexport、dllimport](../../cpp/dllexport-dllimport.md)<br/>
[一般規則和限制](../../cpp/general-rules-and-limitations.md)