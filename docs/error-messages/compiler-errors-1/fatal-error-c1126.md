---
title: 嚴重錯誤 C1126
ms.date: 11/04/2016
f1_keywords:
- C1126
helpviewer_keywords:
- C1126
ms.assetid: f22b26a6-8ad7-47cf-a237-196c8ea60aca
ms.openlocfilehash: 3f4d152163d3b21ddf99644c34e63f35ca15e6e9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62230008"
---
# <a name="fatal-error-c1126"></a>嚴重錯誤 C1126

'identifier': 自動配置超過大小

配置給本機變數的函式 （加上的編譯器，例如額外的 20 個位元組，可切換的函式所使用的空間數量有限） 的空間超過限制。

若要更正這個錯誤，請使用`malloc`或`new`配置大量的資料。