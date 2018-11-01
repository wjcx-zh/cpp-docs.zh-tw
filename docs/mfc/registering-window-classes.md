---
title: 註冊視窗類別
ms.date: 11/04/2016
f1_keywords:
- WndProc
helpviewer_keywords:
- window classes [MFC], registering
- registry [MFC], registering classes
- AfxRegisterWndClass method [MFC]
- MFC, windows
- WinMain method [MFC], and registering window classes
- WndProc method [MFC]
- classes [MFC], registering window classes
- WinMain method [MFC]
- registering window classes [MFC]
ms.assetid: 30994bc4-a362-43da-bcc5-1bf67a3fc929
ms.openlocfilehash: c1fc6628b2b5e8e6fa657f4cf99be2256377a5b1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50540578"
---
# <a name="registering-window-classes"></a>註冊視窗類別

傳統 Windows 程式設計中的視窗「類別」會定義「類別」(而不是 C++ 類別) 的特性，該類別可以建立任意數目的視窗。 這種類別可用於建立視窗的樣板或模型。

## <a name="window-class-registration-in-traditional-programs-for-windows"></a>傳統 Windows 程式中的視窗類別註冊

在 Windows，不以 MFC，傳統程式程序 所有訊息的視窗中其 「 視窗程序 」 或 「`WndProc`。 」A`WndProc`透過 「 視窗類別註冊 」 處理程序與視窗相關聯。 主視窗會在 `WinMain` 函式中進行註冊，而視窗的其他類別則可以在應用程式的任何位置進行註冊。 註冊取決於結構，其中包含一個指向`WndProc`規格游標、 背景筆刷，以及函式等等。 傳遞結構做為參數，以及字串類別的名稱，在先前呼叫`RegisterClass`函式。 因此，註冊類別可由多個視窗共用。

## <a name="window-class-registration-in-mfc-programs"></a>MFC 程式中的視窗類別註冊

相較之下，大部分的視窗類別註冊活動在 MFC 架構程式中會自動完成。 如果您使用 MFC，則通常會使用一般 C++ 語法的類別繼承從現有程式庫類別衍生 C++ 視窗類別。 該架構仍會使用傳統的「註冊類別」，並在您需要時為您提供多個標準的註冊類別。 您可以藉由呼叫註冊其他註冊類別[AfxRegisterWndClass](../mfc/reference/application-information-and-management.md#afxregisterwndclass)全域函式，然後傳遞到已註冊的類別`Create`成員函式`CWnd`。 如此處所述，Windows 的傳統「註冊類別」不會與 C++ 類別混淆。

如需詳細資訊，請參閱 <<c0> [ 技術的附註 1](../mfc/tn001-window-class-registration.md)。

## <a name="see-also"></a>另請參閱

[建立視窗](../mfc/creating-windows.md)

