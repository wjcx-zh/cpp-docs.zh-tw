---
title: C 執行階段錯誤 R6024
ms.date: 11/04/2016
f1_keywords:
- R6024
helpviewer_keywords:
- R6024
ms.assetid: 0fb11c0f-9b81-4cab-81bd-4785742946a5
ms.openlocfilehash: 89b99a93512603eaf2273a6ff3f434f1ad3b3bb8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62214116"
---
# <a name="c-runtime-error-r6024"></a>C 執行階段錯誤 R6024

_onexit/atexit 資料表空間不足

> [!NOTE]
> 如果您遇到這個錯誤訊息時執行應用程式時，應用程式已關閉因為它有內部記憶體問題。 此錯誤通常會造成極低記憶體狀況，很少程式中的 bug 或損毀的視覺效果C++，它會使用程式庫。
>
> 您可以嘗試進行下列步驟來修正這個錯誤：
>
> - 關閉其他正在執行的應用程式或重新啟動電腦以釋出記憶體。
> - 使用**應用程式和功能**或是**程式和功能**頁面**控制台**修復或重新安裝程式。
> - 使用**應用程式和功能**或是**程式和功能**頁面**控制台**修復或重新安裝 Microsoft Visual 的所有副本C++可轉散發套件。
> - 請檢查**Windows Update**中**控制台**軟體更新。
> - 檢查應用程式的更新版本。 如果問題持續發生，請連絡應用程式廠商。

**適用於程式設計人員的資訊**

會發生這個錯誤，因為沒有任何記憶體可供`_onexit`或`atexit`函式。 此錯誤被因為記憶體不足的狀況。 您可以考慮在記憶體不足狀況的預先配置的緩衝區，可協助將使用者資料儲存及執行全新的應用程式的應用程式啟動時結束。