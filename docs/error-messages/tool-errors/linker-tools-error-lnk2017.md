---
title: 連結器工具錯誤 LNK2017
ms.date: 11/04/2016
f1_keywords:
- LNK2017
helpviewer_keywords:
- LNK2017
ms.assetid: f7c21733-b0fb-4888-a295-9b453ba6ee77
ms.openlocfilehash: 02e80de5c34809a331003f3b0fb28d32e138a531
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80194729"
---
# <a name="linker-tools-error-lnk2017"></a>連結器工具錯誤 LNK2017

' symbol ' 重新配置至 ' segment ' 無效，沒有/LARGEADDRESSAWARE：否

您正嘗試建立具有32位位址的64位映射。 若要進行此動作，您必須：

- 使用固定的載入位址。

- 將映射限制為 3 GB。

- 指定[/largeaddressaware： no](../../build/reference/largeaddressaware-handle-large-addresses.md)。
