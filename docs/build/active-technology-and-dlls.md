---
title: Active 技術和 DLL
ms.date: 11/04/2016
helpviewer_keywords:
- in-process server DLLs
- Automation [C++], DLLs
- DLLs [C++], Active Technology
- Active technology [C++]
- MFC DLLs [C++], Active Technology
ms.assetid: 3ed27f8d-164a-4562-ad61-9f2333404cc7
ms.openlocfilehash: f67fb9548601ac705ceda08d20d3049f0bf1e0a5
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2019
ms.locfileid: "65221007"
---
# <a name="active-technology-and-dlls"></a>Active 技術和 DLL

Active 技術可讓物件伺服程式完全實作於 DLL 內。 此類型的伺服器稱為同處理序伺服器。 MFC 不完全支援同處理序伺服器的視覺化編輯的所有功能主要是因為 Active 技術不提供伺服器連結到容器的主要訊息迴圈的方式。 MFC 會需要存取容器應用程式的訊息迴圈來處理快速鍵和閒置時間處理。

如果您正在撰寫 Automation 伺服程式，而且您的伺服器有沒有使用者介面，您可以讓 server 同處理序伺服器，並將它完全放入 DLL。

## <a name="what-do-you-want-to-know-more-about"></a>您還想知道關於哪些方面的詳細資訊？

- [Automation 伺服程式](../mfc/automation-servers.md)

## <a name="see-also"></a>另請參閱

[建立 C /C++在 Visual Studio 中的 Dll](dlls-in-visual-cpp.md)
