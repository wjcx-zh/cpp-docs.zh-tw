---
title: C 執行階段錯誤 R6017
ms.date: 11/04/2016
f1_keywords:
- R6017
helpviewer_keywords:
- R6017
ms.assetid: df3ec5f5-6771-4648-ba06-0e26c6a1cc6a
ms.openlocfilehash: 2d868939425c11f13dffd84e28c1afee45e3b11a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80197298"
---
# <a name="c-runtime-error-r6017"></a>C 執行階段錯誤 R6017

非預期的多執行緒鎖定錯誤

> [!NOTE]
> 如果您在執行應用程式時遇到此錯誤訊息，則應用程式已關閉，因為它有內部問題。 有幾個可能的原因會造成此錯誤，但通常是因為應用程式的程式碼發生瑕疵。
>
> 您可以嘗試進行下列步驟來修正這個錯誤：
>
> - 使用 [**控制台**] 中的 [**應用程式和功能**] 或 [**程式和功能**] 頁面修復或重新安裝程式。
> - 在 [**控制台**] 中選取 [軟體更新] **Windows Update** 。
> - 檢查應用程式的更新版本。 如果問題持續發生，請洽詢應用程式廠商。

**程式設計人員的資訊**

進程在嘗試存取系統資源的 C 執行時間多執行緒鎖定時，收到意外的錯誤。 如果進程不小心改變執行時間堆積資料，通常會發生這個錯誤。 不過，它也可能是因為執行時間程式庫或作業系統程式碼中的內部錯誤所造成。

若要修正此問題，請檢查程式碼中的堆積損毀錯誤。 如需詳細資訊和範例，請參閱[CRT Debug 堆積 Details](/visualstudio/debugger/crt-debug-heap-details)。 接下來，請檢查您是否為應用程式部署使用最新的可轉散發套件。 如需相關資訊，請參閱[在 Visual C++中部署](../../windows/deployment-in-visual-cpp.md)。
