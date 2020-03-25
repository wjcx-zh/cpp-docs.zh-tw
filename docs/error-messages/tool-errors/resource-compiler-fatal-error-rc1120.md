---
title: 資源編譯器嚴重錯誤 RC1120
ms.date: 11/04/2016
f1_keywords:
- RC1120
helpviewer_keywords:
- RC1120
ms.assetid: 4e462931-e42e-42e3-8bfc-847677194286
ms.openlocfilehash: 855a76ff63145695a7063944701d7acc684e0084
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80173006"
---
# <a name="resource-compiler-fatal-error-rc1120"></a>資源編譯器嚴重錯誤 RC1120

記憶體不足，需要的數位位元組

資源編譯器會針對它儲存在其堆積中的專案，用盡儲存空間。 這通常是因為有太多符號的結果。

### <a name="to-fix-by-using-the-following-possible-solutions"></a>使用下列可能的解決方式來進行修正

1. 增加 Windows 交換檔案空間。 如需增加交換檔案空間的詳細資訊，請參閱 Windows 說明中的虛擬記憶體。

1. 排除不必要的 include 檔案，特別是不需要的 `#define`s 和函式原型。

1. 將目前檔案分割成兩個或多個檔案，並分別進行編譯。

1. 移除系統中執行的其他程式或驅動程式，這可能會耗用大量的記憶體。
