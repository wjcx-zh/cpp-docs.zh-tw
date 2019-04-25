---
title: C 執行階段錯誤 R6017
ms.date: 11/04/2016
f1_keywords:
- R6017
helpviewer_keywords:
- R6017
ms.assetid: df3ec5f5-6771-4648-ba06-0e26c6a1cc6a
ms.openlocfilehash: 45f3b07f540cb72a955b19420130a5a806b750d7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62299656"
---
# <a name="c-runtime-error-r6017"></a>C 執行階段錯誤 R6017

未預期的多執行緒鎖定錯誤

> [!NOTE]
> 如果您遇到這個錯誤訊息時執行應用程式時，應用程式已關閉發生內部問題。 有幾個可能的原因，這個錯誤，但通常出自於應用程式的程式碼的缺失。
>
> 您可以嘗試進行下列步驟來修正這個錯誤：
>
> - 使用**應用程式和功能**或是**程式和功能**頁面**控制台**修復或重新安裝程式。
> - 請檢查**Windows Update**中**控制台**軟體更新。
> - 檢查應用程式的更新版本。 如果問題持續發生，請連絡應用程式廠商。

**適用於程式設計人員的資訊**

程序嘗試存取系統資源上的 C 執行階段執行緒鎖定時，收到未預期的錯誤。 如果不小心改變程序的執行階段堆積資料，通常會發生此錯誤。 不過，它也會造成執行階段程式庫或作業系統的程式碼中發生內部錯誤。

若要修正此問題，請檢查程式碼中的堆積損毀錯誤。 如需詳細資訊和範例，請參閱 < [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details)。 接下來，請檢查您的應用程式部署會使用最新的可轉散發套件。 如需資訊，請參閱[視覺效果中的部署C++ ](../../windows/deployment-in-visual-cpp.md)。