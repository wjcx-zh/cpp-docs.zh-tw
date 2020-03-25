---
title: 專案建置警告 PRJ0041
ms.date: 11/04/2016
f1_keywords:
- PRJ0041
helpviewer_keywords:
- PRJ0041
ms.assetid: dc9f4cf9-6bd5-4222-89e8-7802a59bb96b
ms.openlocfilehash: bb6469b1daf193223a9b3361cc3e4bfb96d0c751
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80191924"
---
# <a name="project-build-warning-prj0041"></a>專案建置警告 PRJ0041

找不到檔案 ' file ' 的遺漏相依性 ' dependency '。 您的專案可能仍會建立，但可能會繼續顯示，直到找到此檔案為止。

例如，檔案（資源檔或 .idl/odl 檔案包含專案系統無法解析的 include 語句）。

因為專案系統不會處理預處理器語句（例如 #if），所以違規的語句實際上可能不是組建的一部分。

若要解決這個警告，請刪除 .rc 檔中所有不必要的程式碼，或加入適當名稱的預留位置檔案。
