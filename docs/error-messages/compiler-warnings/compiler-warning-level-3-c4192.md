---
title: 編譯器警告 （層級 3） C4192
ms.date: 11/04/2016
f1_keywords:
- C4192
helpviewer_keywords:
- C4192
ms.assetid: ea5f91fa-8c96-4f3f-ac42-0c8a86d4e5df
ms.openlocfilehash: 56b27596296b87edcc6de406e7b6621d5723815d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62402225"
---
# <a name="compiler-warning-level-3-c4192"></a>編譯器警告 （層級 3） C4192

自動排除時匯入類型程式庫 'library' 的 'name'

A`#import`程式庫包含的項目，*名稱*，也就是也在 Win32 系統標頭中定義。 由於型別程式庫的限制，之類的名稱**IUnknown**或 GUID 通常定義在型別程式庫中複製的系統標頭的定義。 `#import` 會偵測這些項目，並拒絕將它們併入.tlh 和.tli 標頭檔案中。

若要覆寫此行為，請使用`#import`屬性[no_auto_exclude](../../preprocessor/no-auto-exclude.md)並[include （)](../../preprocessor/include-parens.md)。