---
title: 嚴重錯誤 C1210
ms.date: 11/04/2016
f1_keywords:
- C1210
helpviewer_keywords:
- C1210
ms.assetid: e2208309-c284-425c-a7e8-48e96e66f35b
ms.openlocfilehash: 50bafa522c931c909b5ce163a78305ffc028765a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80203381"
---
# <a name="fatal-error-c1210"></a>嚴重錯誤 C1210

> 所安裝的執行階段版本不支援 /clr:pure 和 /clr:safe

**/Clr： pure**和 **/clr： safe**編譯器選項在 Visual Studio 2015 中已被取代，在 Visual Studio 2017 中不支援。

如果您有目前版本的編譯器，但 Common Language Runtime 來自舊版本，就會發生 C1210。

編譯器的某個功能可能無法在執行階段的舊版本上運作。

若要解決 C1210，請安裝要與編譯器搭配使用的 Common Language Runtime 版本。
