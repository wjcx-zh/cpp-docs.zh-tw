---
title: C 執行階段錯誤 R6030
ms.date: 11/04/2016
f1_keywords:
- R6030
helpviewer_keywords:
- R6030
ms.assetid: 0238a6c3-a033-4046-8adc-f8f99d961153
ms.openlocfilehash: 5d7160623d4e1eb83240c09e637c780fefc0d43d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80197115"
---
# <a name="c-runtime-error-r6030"></a>C 執行階段錯誤 R6030

CRT 未初始化

> [!NOTE]
> 如果您在執行應用程式時遇到此錯誤訊息，則應用程式已關閉，因為它有內部問題。 此問題最常發生于特定的安全性軟體程式，或很少因程式中的錯誤而造成。
>
> 您可以嘗試進行下列步驟來修正這個錯誤：
>
> - 您的安全性軟體可能會有特定的指示來減輕這個問題。 如需詳細資訊，請參閱安全性軟體廠商的網站。 或者，請檢查您的安全性軟體的更新版本，或嘗試不同的安全性軟體。
> - 使用 [**控制台**] 中的 [**應用程式和功能**] 或 [**程式和功能**] 頁面修復或重新安裝程式。
> - 在 [**控制台**] 中選取 [軟體更新] **Windows Update** 。
> - 檢查應用程式的更新版本。 如果問題持續發生，請洽詢應用程式廠商。

**程式設計人員的資訊**

如果您使用 C 執行時間（CRT），但未執行 CRT 啟動程式碼，就會發生這個錯誤。 如果連結器切換[/ENTRY](../../build/reference/entry-entry-point-symbol.md)是用來覆寫主控台 exe 的預設起始位址（通常是**mainCRTStartup**、 **WmainCRTStartup** 、Windows exe 的**WinMainCRTStartup**或**wWinMainCRTStartup** ），或 DLL 的 **_DllMainCRTStartup** ，就可能會發生這個錯誤。 除非在啟動時呼叫上述函式的其中一個，否則 C 執行時間不會初始化。 當您連結至 C 執行時間程式庫並使用一般**main**、 **wmain**、 **WinMain**或**DllMain**進入點時，預設會呼叫這些啟動功能。

當另一個程式使用程式碼插入技術來攔截某些 DLL 程式庫呼叫時，也可能會發生此錯誤。 有些侵入式安全性程式會使用這項技術。 在 Visual Studio 2015 之前C++的 Visual 版本中，可以使用靜態連結的 CRT 程式庫來解決問題，但基於安全性和應用程式更新的理由，不建議這樣做。 修正此問題可能需要使用者動作。
