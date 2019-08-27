---
title: 嚴重錯誤 C1010
ms.date: 08/19/2019
f1_keywords:
- C1010
helpviewer_keywords:
- C1010
ms.assetid: dfd035f1-a7a2-40bc-bc92-dc4d7f456767
ms.openlocfilehash: 35b0f60f7eb3be887598e7ffaf3e3eae74aefcff
ms.sourcegitcommit: 9d4ffb8e6e0d70520a1e1a77805785878d445b8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/20/2019
ms.locfileid: "69630790"
---
# <a name="fatal-error-c1010"></a>嚴重錯誤 C1010

尋找先行編譯的標頭時出現非預期的檔案結尾。 您是否忘了將「#include 名稱」新增至您的來源？

原始程式檔中未列出使用[/yu](../../build/reference/yu-use-precompiled-header-file.md)指定的 include 檔案。  在大部分的 Visual Studio C++專案類型和*pch*中, 預設會啟用此選項 (Visual Studio 2017 和更早版本中的*stdafx.h* ) 是此選項所指定的預設 include 檔案。

在 Visual Studio 環境中, 請使用下列其中一種方法來解決此錯誤:

- 如果您未在專案中使用先行編譯的標頭, 請將原始程式檔的**Create/use 先行編譯頭**檔設定為**不要使用先行編譯的標頭**。 若要設定這個編譯器選項, 請遵循下列步驟:

   1. 在專案的 [方案總管] 窗格中, 以滑鼠右鍵按一下專案名稱, 然後按一下 [**屬性**]。

   1. 在左窗格中, 按一下 [ **C/C++**  ] 資料夾。

   1. 按一下 [先行**編譯頭**檔] 節點。

   1. 在右窗格中, 按一下 [**建立/使用先行編譯頭**檔], 然後按一下 [**不使用先行編譯頭**檔]。

- 請確定您並未不慎刪除、重新命名或移除目前專案中的標頭檔 (預設為 stdafx.h)。 這個檔案也必須包含在原始程式檔中使用 **#include "stdafx.h**" 的任何其他程式碼之前。 (此標頭檔已指定為透過檔案專案屬性**建立/使用 PCH** )