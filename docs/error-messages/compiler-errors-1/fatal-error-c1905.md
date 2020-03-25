---
title: 嚴重錯誤 C1905
ms.date: 11/04/2016
f1_keywords:
- C1905
helpviewer_keywords:
- C1905
ms.assetid: fefc6769-477f-45a2-9878-6f0a5f42472c
ms.openlocfilehash: 106dfe8a078047225097686d185a1ba43987ce33
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80202619"
---
# <a name="fatal-error-c1905"></a>嚴重錯誤 C1905

前端和後端不相容 (必須以相同處理器為目標)

當以一個處理器為目標的編譯器前端（C1 .dll）（例如 x86、ARM 或 x64）產生 .obj 檔案，但以不同處理器為目標的後端（C2 .dll）所讀取時，就會發生此錯誤。

若要修正這個問題，請確定您使用相符的前端和後端。 這是在 Visual Studio 中所建立專案的預設值。 如果您有編輯專案檔，並使用編譯器工具的不同路徑，可能會發生這個錯誤。 如果您沒有特別設定編譯器工具的路徑，則如果您的 Visual Studio 安裝已損毀，就可能會發生這個錯誤。 比方說，您可能將編譯器 .dll 檔案由一個位置複製到另一個位置。 使用 Windows [控制台] 中的 [**程式和功能**] 來修復或重新安裝 Visual Studio。
