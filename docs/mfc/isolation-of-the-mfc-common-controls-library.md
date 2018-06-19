---
title: 隔離的 MFC 通用控制項程式庫 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC, Common Controls library
ms.assetid: 7471e6f0-49b0-47f7-86e7-8d6bc3541694
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 193a0ea527cda3819a585f5b7149c823a7eb8ef7
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33346811"
---
# <a name="isolation-of-the-mfc-common-controls-library"></a>MFC 通用控制項程式庫的隔離
通用控制項程式庫現在在 MFC 中是隔離的，可讓不同的模組 (例如，使用者 DLL) 透過在其資訊清單中指定版本，來使用不同版本的通用控制項程式庫。  
  
 MFC 應用程式 （或由 MFC 呼叫使用者程式碼） 會呼叫名為應用程式開發介面透過包裝函式的通用控制項程式庫`Afx` *FunctionName*，其中*FunctionName*的一般名稱應用程式開發介面的控制項。 這些包裝函式是在 afxcomctl32.h 和 afxcomctl32.inl 中定義。  
  
 您可以使用[AFX_COMCTL32_IF_EXISTS](reference/run-time-object-model-services.md#afx_comctl32_if_exists)和[AFX_COMCTL32_IF_EXISTS2](reference/run-time-object-model-services.md#afx_comctl32_if_exists2)巨集 (定義在 afxcomctl32.h)，以判斷通用控制項程式庫是否實作特定 API，而不是呼叫[GetProcAddress](../build/getprocaddress.md)。  
  
 技術上來說，您是透過包裝函式類別 `CComCtlWrapper` (在 afxcomctl32.h 中定義) 呼叫通用控制項程式庫 API。 `CComCtlWrapper` 也負責載入和卸載 comctl32.dll。 MFC 模組狀態包含 `CComCtlWrapper` 執行個體的指標。 您可以使用 `afxComCtlWrapper` 巨集來存取包裝函式類別。  
  
 請注意，直接從 MFC 應用程式或使用者 DLL 呼叫通用控制項 API (不使用 MFC 包裝函式) 在許多情況下可以運作，因為 MFC 應用程式或使用者 DLL 是繫結至其在資訊清單中要求的通用控制項程式庫。 不過，因為 MFC 程式碼可能是以不同的通用控制項程式庫版本從使用者 DLL 呼叫，所以 MFC 程式碼本身必須使用包裝函式。

