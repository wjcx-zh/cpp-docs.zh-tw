---
title: 嚴重錯誤 C1210 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1210
dev_langs:
- C++
helpviewer_keywords:
- C1210
ms.assetid: e2208309-c284-425c-a7e8-48e96e66f35b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4d22a34f44fb2c97fe341cb313d7917a35506cdd
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2018
ms.locfileid: "34704980"
---
# <a name="fatal-error-c1210"></a>嚴重錯誤 C1210

> 所安裝的執行階段版本不支援 /clr:pure 和 /clr:safe

**/Clr: pure**和 **/clr: safe**編譯器選項都是 Visual Studio 2015 中已被取代，並不支援的 Visual Studio 2017 中。

如果您有目前版本的編譯器，但 Common Language Runtime 來自舊版本，就會發生 C1210。

編譯器的某個功能可能無法在執行階段的舊版本上運作。

若要解決 C1210，請安裝要與編譯器搭配使用的 Common Language Runtime 版本。