---
title: 應用程式架構
ms.date: 11/04/2016
helpviewer_keywords:
- application framework [MFC], building applications
- applications [MFC]
- application framework [MFC]
ms.assetid: 912684e6-4418-49dc-9877-a4cd19d69d20
ms.openlocfilehash: 3d6616380e9461489d208281a34e0b0b4aa2caf0
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84626009"
---
# <a name="application-framework"></a>應用程式架構

MFC 程式庫的核心是以 C++ 形式封裝大部分的 Windows API。 程式庫類別代表視窗、對話方塊、裝置內容、通用 GDI 物件 (例如筆刷、畫筆、控制項和其他標準 Windows 項目)。 這些類別會將方便的 C++ 成員函式介面提供給所封裝的 Windows 結構。 如需使用這些類別的詳細資訊，請參閱[視窗物件主題](window-objects.md)。

但是，MFC 程式庫也提供在 Windows API 的 C++ 封裝建立的其他應用程式功能層。 此層是 Windows 應用程式架構，可提供 Windows 程式最常見的一般使用者介面，包括工具列、狀態列、列印、列印預覽、資料庫支援和 ActiveX 支援。 [使用類別來撰寫適用于 Windows 的應用程式](using-the-classes-to-write-applications-for-windows.md)會詳細說明架構。

## <a name="see-also"></a>另請參閱

[一般類別設計原理](general-class-design-philosophy.md)
