---
title: STL/CLR 容器項目的需求
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- C++ Standard Library, template class containers
- STL/CLR, containers
- containers, STL/CLR
- containers, C++ Standard Library
ms.assetid: 59ab240c-15bf-4701-a9f9-e7c56e5ab53f
ms.openlocfilehash: 0744d38a08dbd972b786e1cc74c112322ecf181f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50428570"
---
# <a name="requirements-for-stlclr-container-elements"></a>STL/CLR 容器項目的需求

插入 STL/CLR 容器的所有參考類型至少必須擁有下列項目：

- 公用的複製建構函式。

- 公用的指派運算子。

- 公用的解構函式。

此外，這類的關聯容器[設定](../dotnet/set-stl-clr.md)並[地圖](../dotnet/map-stl-clr.md)必須具有公用的比較運算子定義，也就是`operator<`預設。 容器的某些作業可能也需要公用預設建構函式和公用等價運算子定義。

和參考類型一樣，實值類型及要插入一個關聯容器之參考類型的控制代碼必須具有比較運算子，例如 `operator<` 定義。 公用複製建構函式、公用指派運算子和公用解構函式的需求中未包含實值類型或參考類型的控制代碼。

## <a name="see-also"></a>另請參閱

[C++ 標準程式庫參考](../standard-library/cpp-standard-library-reference.md)