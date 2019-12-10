---
title: 命令列警告 D9043
ms.date: 11/04/2016
f1_keywords:
- D9043
helpviewer_keywords:
- D9043
ms.assetid: 9263e28d-217b-414c-bfb6-86efd3c27a77
ms.openlocfilehash: 747f3cadd050b8f36c13fd28ae123f7a6dbdfb05
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2019
ms.locfileid: "74992092"
---
# <a name="command-line-warning-d9043"></a>命令列警告 D9043

' compiler_option ' 的值 ' warning_level ' 無效;假設為 ' 4999 ';程式碼分析警告未與警告層級相關聯

## <a name="example"></a>範例

下列範例會產生 C9043。

```cpp
// D9043.cpp
// compile with: /analyze /w16001
// D9043 warning expected
int main() {}
```
