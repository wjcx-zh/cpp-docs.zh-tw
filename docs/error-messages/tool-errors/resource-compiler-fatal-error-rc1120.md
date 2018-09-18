---
title: 資源編譯器嚴重錯誤 RC1120 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- RC1120
dev_langs:
- C++
helpviewer_keywords:
- RC1120
ms.assetid: 4e462931-e42e-42e3-8bfc-847677194286
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 62f28e381d4eac0bfd1f010ef3919452635a1b96
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46056998"
---
# <a name="resource-compiler-fatal-error-rc1120"></a>資源編譯器嚴重錯誤 RC1120

因為記憶體不足、 所需的位元組數目

資源編譯器已用完存放裝置，它會儲存在堆積 （heap） 中的項目。 這通常是有太多符號的結果。

### <a name="to-fix-by-using-the-following-possible-solutions"></a>使用下列可能的解決方式來進行修正

1. 增加 Windows 交換檔案空間。 如需有關如何增加分頁檔空間的詳細資訊，請參閱 Windows 說明中的虛擬記憶體。

1. 排除不必要 include 檔案，特別是不必要的`#define`s 和函式的原型。

1. 目前的檔案分割成兩個或多個檔案，然後分別進行編譯。

1. 移除其他程式或系統，可能會消耗大量的記憶體中執行的驅動程式。