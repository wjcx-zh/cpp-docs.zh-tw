---
title: 嚴重錯誤 C1010
ms.date: 11/04/2016
f1_keywords:
- C1010
helpviewer_keywords:
- C1010
ms.assetid: dfd035f1-a7a2-40bc-bc92-dc4d7f456767
ms.openlocfilehash: 204c7ef94d82513338f6635ec9eb22f26fc090a7
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2019
ms.locfileid: "65448027"
---
# <a name="fatal-error-c1010"></a>嚴重錯誤 C1010

尋找先行編譯的標頭時出現非預期的檔案結尾。 您是否忘記新增 '#include 名稱' 到您的來源？

使用指定的 include 檔案[/Yu](../../build/reference/yu-use-precompiled-header-file.md)未列在原始程式檔。  會啟用此選項大部分的 Visual Studio 中的預設C++專案類型和"stdafx.h"是預設值包括這個選項所指定的檔案。

在 Visual Studio 環境中，使用下列方法之一來解決這個錯誤：

- 如果您未使用先行編譯標頭中您的專案，設定**建立/使用先行編譯標頭**屬性的原始程式檔必須**未使用先行編譯標頭**。 若要設定這個編譯器選項，請遵循下列步驟：

   1. 在方案總管 窗格中的專案，以滑鼠右鍵按一下專案名稱，然後**屬性**。

   1. 在左窗格中，按一下**C /C++** 資料夾。

   1. 按一下 **先行編譯標頭**節點。

   1. 在右窗格中，按一下**建立/使用先行編譯標頭**，然後按一下**未使用先行編譯標頭**。

- 請確定您不小心刪除、 重新命名或移除標頭檔 (根據預設，stdafx.h) 從目前的專案。 此檔案也必須使用的原始程式檔中的任何其他程式碼之前包含 **#include"stdafx.h"**。 (此標頭檔指定為**透過檔案建立/使用 PCH**專案屬性)