---
title: 註冊視窗類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- WndProc
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 00e397f8880f6f42f1930e668b64d3ba62eb2c64
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33379738"
---
# <a name="registering-window-classes"></a>註冊視窗類別
傳統 Windows 程式設計中的視窗「類別」會定義「類別」(而不是 C++ 類別) 的特性，該類別可以建立任意數目的視窗。 這種類別可用於建立視窗的樣板或模型。  
  
## <a name="window-class-registration-in-traditional-programs-for-windows"></a>傳統 Windows 程式中的視窗類別註冊  
 對於 Windows，而非 MFC，傳統程式處理所有訊息的視窗中其 「 視窗程序 」 或 「**WndProc**。 」 A **WndProc**與視窗，以透過 「 視窗類別註冊 」 處理程序相關聯。 主視窗會在 `WinMain` 函式中進行註冊，而視窗的其他類別則可以在應用程式的任何位置進行註冊。 註冊取決於包含指標的結構**WndProc**規格游標、 背景筆刷，以及函式等等。 傳遞結構做為參數，以及字串名稱的類別，以在先前呼叫**RegisterClass**函式。 因此，註冊類別可由多個視窗共用。  
  
## <a name="window-class-registration-in-mfc-programs"></a>MFC 程式中的視窗類別註冊  
 相較之下，大部分的視窗類別註冊活動在 MFC 架構程式中會自動完成。 如果您使用 MFC，則通常會使用一般 C++ 語法的類別繼承從現有程式庫類別衍生 C++ 視窗類別。 該架構仍會使用傳統的「註冊類別」，並在您需要時為您提供多個標準的註冊類別。 您可以藉由呼叫註冊額外的註冊類別[AfxRegisterWndClass](../mfc/reference/application-information-and-management.md#afxregisterwndclass)全域函式，然後再將傳遞至已註冊的類別**建立**成員函式`CWnd`。 如此處所述，Windows 的傳統「註冊類別」不會與 C++ 類別混淆。  
  
 如需詳細資訊，請參閱[技術提示 1](../mfc/tn001-window-class-registration.md)。  
  
## <a name="see-also"></a>另請參閱  
 [建立視窗](../mfc/creating-windows.md)

