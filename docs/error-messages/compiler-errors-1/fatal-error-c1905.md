---
title: 嚴重錯誤 C1905
ms.date: 11/04/2016
f1_keywords:
- C1905
helpviewer_keywords:
- C1905
ms.assetid: fefc6769-477f-45a2-9878-6f0a5f42472c
ms.openlocfilehash: 3fb4db30d91e0dd8c9dbeeebca46210122e5ff07
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50663147"
---
# <a name="fatal-error-c1905"></a>嚴重錯誤 C1905

前端和後端不相容 (必須以相同處理器為目標)

.Obj 檔案是或所產生的編譯器前端 (C1.dll) 該目標的一個處理器，例如 x86、 ARM、 x64，但以不同的處理器為目標的後端 (C2.dll) 讀取時，就會發生此錯誤。

若要修正這個問題，請確定您使用相符的前端和後端。 這是在 Visual Studio 中所建立專案的預設值。 如果您有編輯專案檔，並使用編譯器工具的不同路徑，可能會發生這個錯誤。 如果您沒有特別設定編譯器工具的路徑，則如果您的 Visual Studio 安裝已損毀，就可能會發生這個錯誤。 比方說，您可能將編譯器 .dll 檔案由一個位置複製到另一個位置。 使用**程式和功能**Windows 控制台中修復或重新安裝 Visual Studio。