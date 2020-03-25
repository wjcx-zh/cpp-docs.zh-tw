---
title: BSCMAKE 錯誤 BK1513
ms.date: 11/04/2016
f1_keywords:
- BK1513
helpviewer_keywords:
- BK1513
ms.assetid: 9ba87c09-8d82-4c80-b0cf-a8de63dcf9da
ms.openlocfilehash: 3a16163f33814be18a67833995362ee9b13d8118
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80197635"
---
# <a name="bscmake-error-bk1513"></a>BSCMAKE 錯誤 BK1513

非累加式更新需要所有 .SBR 檔案

BSCMAKE 無法建置新的瀏覽資訊 (.bsc) 檔，因為一個或多個 .sbr 檔遭到截斷。 若要尋找截斷的 .sbr 檔的名稱，請閱讀伴隨此錯誤的[BK4502](../../error-messages/tool-errors/bscmake-warning-bk4502.md)警告。

BSCMAKE 可以將 .bsc 檔更新為遭截斷的 .sbr 檔，但無法建置新的 .bsc 檔。 BSCMAKE 可能會因為下列原因而建置新的 .bsc 檔：

- .bsc 檔遺失。

- 指定給 .bsc 檔的檔案名稱錯誤。

- .bsc 檔損毀。

若要解決這個問題，請刪除被截斷的 .sbr 檔並重新建置，或清除方案並重建。 （在 IDE 中，選擇 [**組建**]、[**清除方案**]，然後選擇 [**組建**]、[**重建方案**]）。
