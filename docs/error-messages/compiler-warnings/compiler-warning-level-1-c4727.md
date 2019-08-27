---
title: 編譯器警告 (層級 1) C4727
ms.date: 08/19/2019
f1_keywords:
- C4727
helpviewer_keywords:
- C4727
ms.assetid: 991b0087-3a50-40f5-9cdb-cdc367cd472c
ms.openlocfilehash: 1bcc029536d2602d50178d7148332b8371db3c7f
ms.sourcegitcommit: 9d4ffb8e6e0d70520a1e1a77805785878d445b8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/20/2019
ms.locfileid: "69630824"
---
# <a name="compiler-warning-level-1-c4727"></a>編譯器警告 (層級 1) C4727

在 obj_file_1 和 obj_file_2 中找到具有相同時間戳記的 PCH 名為 pch_file。  使用第一個 PCH。

> [!NOTE]
> 在 Visual Studio 2017 和更早版本中, 預先編譯的標頭預設稱為*stdafx.h* , 而在 Visual Studio 2019 和更新版本中, 預設會將它稱為*pch。*

使用 **/yc**編譯多個 compilands 時, 以及編譯器能夠標記所有具有相同 .pch 時間戳記的 .obj 檔案時, 就會發生 C4727。

若要解決此問題, 請使用 **/yc/c** (建立 pch) 來編譯一個原始程式檔, 而其他檔案則會與 **/yu/c** (使用 pch) 分開編譯, 然後將它們連結在一起。

因此, 如果您執行了下列動作, 它會產生 C4727:

::: moniker range="<=vs-2017"

**cl/clr/GL a .cpp b .cpp c .cpp/Ycstdafx。h**

您可以改為執行下列動作:

**cl/clr/GL a .cpp/Ycstdafx.h/c**

**cl/clr/GL b. .cpp c .cpp/Yustdafx.h/link a .obj**

::: moniker-end

::: moniker range=">=vs-2019"

**cl/clr/GL a .cpp b .cpp c .cpp/Ycpch。h**

您可以改為執行下列動作:

**cl/clr/GL a .cpp/Ycpch.h/c**

**cl/clr/GL b. .cpp c .cpp/Yupch.h/link a .obj**

::: moniker-end


如需詳細資訊，請參閱

- [/Yc (建立先行編譯標頭檔)](../../build/reference/yc-create-precompiled-header-file.md)

- [/Yu (使用先行編譯標頭檔)](../../build/reference/yu-use-precompiled-header-file.md)