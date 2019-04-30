---
title: 資源編譯器嚴重錯誤 RC1120
ms.date: 11/04/2016
f1_keywords:
- RC1120
helpviewer_keywords:
- RC1120
ms.assetid: 4e462931-e42e-42e3-8bfc-847677194286
ms.openlocfilehash: eff46ddee118c3355e548c73220b407db0561e36
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62374246"
---
# <a name="resource-compiler-fatal-error-rc1120"></a>資源編譯器嚴重錯誤 RC1120

因為記憶體不足、 所需的位元組數目

資源編譯器已用完存放裝置，它會儲存在堆積 （heap） 中的項目。 這通常是有太多符號的結果。

### <a name="to-fix-by-using-the-following-possible-solutions"></a>使用下列可能的解決方式來進行修正

1. 增加 Windows 交換檔案空間。 如需有關如何增加分頁檔空間的詳細資訊，請參閱 Windows 說明中的虛擬記憶體。

1. 排除不必要 include 檔案，特別是不必要的`#define`s 和函式的原型。

1. 目前的檔案分割成兩個或多個檔案，然後分別進行編譯。

1. 移除其他程式或系統，可能會消耗大量的記憶體中執行的驅動程式。