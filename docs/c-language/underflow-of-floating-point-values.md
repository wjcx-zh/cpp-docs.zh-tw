---
title: 浮點值反向溢位
ms.date: 11/04/2016
ms.assetid: 78af8016-643c-47db-b4f1-7f06cb4b243e
ms.openlocfilehash: 93230b50b81ede44a9c55406db1566df2660c1ba
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/24/2019
ms.locfileid: "64344054"
---
# <a name="underflow-of-floating-point-values"></a>浮點值反向溢位

**ANSI 4.5.1** 數學函式是否在反向溢位範圍錯誤上將整數運算式 `errno` 設定為巨集 `ERANGE` 的值

浮點反向溢位不會將運算式 `errno` 設定為 `ERANGE`。 當值趨近於零，最終造成反向溢位時，會將其值設定為零。

## <a name="see-also"></a>請參閱

[程式庫函式](../c-language/library-functions.md)
