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
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2019
ms.locfileid: "65221007"
---
# <a name="active-technology-and-dlls"></a>Active 技術和 DLL

主動技術可讓物件服務器在 DLL 內完全實作為。 這種類型的伺服器稱為同進程伺服器。 MFC 並不完全支援所有視覺編輯功能的同進程伺服器，主要是因為使用中的技術並不提供方法讓伺服器連結至容器的主要訊息迴圈。 MFC 需要存取容器應用程式的訊息迴圈，以處理快速鍵和閒置時間處理。

如果您要撰寫 Automation 伺服器，而您的伺服器沒有使用者介面，您可以將伺服器設為內含式伺服器，並將它完全放入 DLL 中。

## <a name="what-do-you-want-to-know-more-about"></a>您還想知道關於哪些方面的詳細資訊？

- [Automation 伺服程式](../mfc/automation-servers.md)

## <a name="see-also"></a>請參閱

[在 Visual Studio 中建立 C++ DLL](dlls-in-visual-cpp.md)
