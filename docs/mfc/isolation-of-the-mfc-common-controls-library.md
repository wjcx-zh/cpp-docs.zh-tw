---
title: MFC 通用控制項程式庫的隔離
ms.date: 11/04/2016
helpviewer_keywords:
- MFC, Common Controls library
ms.assetid: 7471e6f0-49b0-47f7-86e7-8d6bc3541694
ms.openlocfilehash: 94700f850be62404f22974a1d5e76acad711555c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62310860"
---
# <a name="isolation-of-the-mfc-common-controls-library"></a>MFC 通用控制項程式庫的隔離

通用控制項程式庫現在在 MFC 中是隔離的，可讓不同的模組 (例如，使用者 DLL) 透過在其資訊清單中指定版本，來使用不同版本的通用控制項程式庫。

MFC 應用程式 （或 MFC 呼叫的使用者程式碼） 會呼叫 Api 的包裝函式透過名為的通用控制項程式庫`Afx` *FunctionName*，其中*FunctionName*是通用的名稱控制項 API。 這些包裝函式是在 afxcomctl32.h 和 afxcomctl32.inl 中定義。

您可以使用[AFX_COMCTL32_IF_EXISTS](reference/run-time-object-model-services.md#afx_comctl32_if_exists)並[AFX_COMCTL32_IF_EXISTS2](reference/run-time-object-model-services.md#afx_comctl32_if_exists2)巨集 (在 afxcomctl32.h 中)，以判斷通用控制項程式庫是否實作某個 API 而不是呼叫[GetProcAddress](../build/getprocaddress.md)。

技術上來說，您是透過包裝函式類別 `CComCtlWrapper` (在 afxcomctl32.h 中定義) 呼叫通用控制項程式庫 API。 `CComCtlWrapper` 也負責載入和卸載 comctl32.dll。 MFC 模組狀態包含 `CComCtlWrapper` 執行個體的指標。 您可以使用 `afxComCtlWrapper` 巨集來存取包裝函式類別。

請注意，直接從 MFC 應用程式或使用者 DLL 呼叫通用控制項 API (不使用 MFC 包裝函式) 在許多情況下可以運作，因為 MFC 應用程式或使用者 DLL 是繫結至其在資訊清單中要求的通用控制項程式庫。 不過，因為 MFC 程式碼可能是以不同的通用控制項程式庫版本從使用者 DLL 呼叫，所以 MFC 程式碼本身必須使用包裝函式。
