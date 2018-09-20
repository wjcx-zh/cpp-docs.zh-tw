---
title: SDI 和 MDI |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- frame windows [MFC], SDI applications
- frame windows [MFC], MDI applications
- MFC, windows
- single document interface (SDI) [MFC], applications
- MDI [MFC], vs. SDI
ms.assetid: bb7239d9-4759-4f63-bfff-44a04b48c067
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8189af7939bfca0fd206fa72892098e373444879
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46401442"
---
# <a name="sdi-and-mdi"></a>SDI 和 MDI

MFC 可讓您輕鬆地使用單一文件介面 (SDI) 和多重文件介面 (MDI) 應用程式。

SDI 應用程式可讓一次只能有一個開啟的文件框架視窗。 MDI 應用程式允許多個文件框架視窗，在相同的執行個體的應用程式中開啟。 MDI 應用程式有的視窗內的多個 MDI 子視窗，也就是本身的框架視窗，即可開啟，每個都包含個別的文件。 在某些應用程式中，子視窗可以是不同的類型，例如圖表視窗和試算表的視窗。 在此情況下，會啟用不同類型的 MDI 子視窗，可以變更功能表列。

> [!NOTE]
>  在 Windows 95 和更新版本，但應用程式通常是 SDI 因為作業系統已採用 」 的文件為中心 」 檢視。

如需詳細資訊，請參閱 <<c0> [ 文件、 檢視和架構](../mfc/documents-views-and-the-framework.md)。

## <a name="see-also"></a>另請參閱

[使用類別來編寫 Windows 應用程式](../mfc/using-the-classes-to-write-applications-for-windows.md)
