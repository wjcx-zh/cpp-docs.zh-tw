---
title: 開發您自己的 Helper 函式
ms.date: 11/04/2016
helpviewer_keywords:
- helper functions
ms.assetid: a845429d-68b1-4e14-aa88-f3f5343bd490
ms.openlocfilehash: 73b4a8180345dd6f7dc26f4243f6e63eda80e4af
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62293793"
---
# <a name="developing-your-own-helper-function"></a>開發您自己的 Helper 函式

若要提供自己進行匯入之 DLL 的名稱為基礎的特定處理常式的版本。 這麼做的兩種方法： 程式碼撰寫您自己，可能會根據提供的程式碼，或只將連結所提供的版本，使用先前說明的告知攔截。

## <a name="code-your-own"></a>程式碼自己

這是相當簡單，因為您基本上可以使用做為指導方針提供的程式碼，新的帳戶。 當然，它必須遵守的呼叫慣例，如果它傳回給連結器產生的 thunk，它必須傳回適當的函式指標。 一次在您的程式碼中，您可以執行幾乎任何您想要以滿足呼叫或取得的呼叫。

## <a name="use-the-start-processing-notification-hook"></a>使用啟動處理通知攔截

此外，它可能會最簡單的方式只需提供新的指標，以使用者提供通知攔截函式，用來接收通知 dliStartProcessing 上的預設協助程式相同的值。 此時，攔截函式可以基本上會變成新的協助程式函數，因為成功傳回時預設協助程式會略過所有其他預設協助程式中處理。

## <a name="see-also"></a>另請參閱

[延遲載入 DLL 的連結器支援](linker-support-for-delay-loaded-dlls.md)
