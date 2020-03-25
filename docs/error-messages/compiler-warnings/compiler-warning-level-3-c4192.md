---
title: 編譯器警告（層級3） C4192
ms.date: 11/04/2016
f1_keywords:
- C4192
helpviewer_keywords:
- C4192
ms.assetid: ea5f91fa-8c96-4f3f-ac42-0c8a86d4e5df
ms.openlocfilehash: 38b346e0a90729bda431b9cb578a03806be1ea4c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80198974"
---
# <a name="compiler-warning-level-3-c4192"></a>編譯器警告（層級3） C4192

匯入類型程式庫 ' library ' 時自動排除 ' name '

`#import` 程式庫包含一個專案，也就是在 Win32 系統標頭中定義的*名稱*。 由於類型程式庫的限制，通常會在類型程式庫中定義**IUnknown**或 GUID 之類的名稱，並複製系統標頭中的定義。 `#import` 將會偵測到這些專案，並拒絕將它們併入 tlh 和. .tli 標頭檔中。

若要覆寫此行為，請使用 `#import` 屬性[no_auto_exclude](../../preprocessor/no-auto-exclude.md)並[包含（）](../../preprocessor/include-parens.md)。
