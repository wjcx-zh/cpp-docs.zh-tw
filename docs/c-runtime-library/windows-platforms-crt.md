---
title: Windows 平台 (CRT) | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2018
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- c.programs
dev_langs:
- C++
helpviewer_keywords:
- CRT, compatibility
- backward compatibility [C++], C run-time libraries
- compatibility [C++], C run-time libraries
- MBCS [C++], Win32 platforms
- operating systems [C++]
- Unicode [C++], Win32 platforms
ms.assetid: 0aacaf45-6dc4-4908-bd52-57abac7b39f6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d53e8020bbb7649d78232025ef9c63c1dc868fee
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32409003"
---
# <a name="windows-platforms-crt"></a>Windows 平台 (CRT)

Visual Studio 的 C 執行階段程式庫支援 Windows 與 Windows Server 目前的版本：[!INCLUDE[win8](../build/reference/includes/win8_md.md)]、[!INCLUDE[winserver8](../build/reference/includes/winserver8_md.md)]、[!INCLUDE[win7](../build/includes/win7_md.md)]、[!INCLUDE[winsvr08](../build/reference/includes/winsvr08_md.md)]與 Windows Vista，並選擇性支援[!INCLUDE[winxp](../build/includes/winxp_md.md)] 適用於 x86 的 Service Pack 3 (SP3)、[!INCLUDE[winxp](../build/includes/winxp_md.md)] 適用於 x64 的 Service Pack 2 (SP2) 與 [!INCLUDE[WinXPSvr](../build/includes/winxpsvr_md.md)] 適用於 x86 與 x64 的 Service Pack 2 (SP2)。 這些作業系統全都支援 Windows 傳統型 API (Win32) 並提供 Unicode 支援。 此外，任何 Win32 應用程式都可以使用多位元組字元集 (MBCS)。

> [!NOTE]
> Visual Studio 2017 中**使用 C++ 的桌面開發**工作負載預設安裝並不包含 [!INCLUDE[winxp](../build/includes/winxp_md.md)] 與 [!INCLUDE[WinXPSvr](../build/includes/winxpsvr_md.md)] 開發的支援。 您必須安裝選用元件 **C++ 的 Windows XP 支援**才能啟用 Windows XP 平台工具組。

## <a name="see-also"></a>另請參閱

[相容性](../c-runtime-library/compatibility.md)  
