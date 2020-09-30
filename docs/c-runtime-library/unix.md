---
title: UNIX
description: 將程式移植至 Unix 的指導方針。
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- unix
helpviewer_keywords:
- UNIX
- POSIX compatibility
- POSIX file names
- UNIX, compatibility
ms.assetid: 40792414-7a5b-415d-bfa8-2bfb1ebb3731
ms.openlocfilehash: 07f5ffeec8696ded5880c45ed2ea1a5107bee48c
ms.sourcegitcommit: 9451db8480992017c46f9d2df23fb17b503bbe74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/30/2020
ms.locfileid: "91590143"
---
# <a name="unix"></a>UNIX

若計畫將您的程式移植到 UNIX，請依照這些指導方針執行：

- 請勿從 SYS 子目錄移除標頭檔。 只有當您不打算將程式傳輸至 UNIX 時，才可以將 SYS 標頭檔放在其他位置。

- 在接受使用代表路徑與檔案名稱的字串作為引數的常式中使用 UNIX 相容路徑分隔符號。 UNIX 針對此目的僅支援正斜線 (/) ，但 Win32 作業系統支援反斜線 (\\) 和正斜線 (/) 。 例如，本檔使用 UNIX 相容的正斜線作為語句中的路徑分隔符號 `#include` 。  (不過，Windows 作業系統命令 shell （CMD.EXE）不支援在命令提示字元中輸入命令的正斜線。 ) 

- 使用在 UNIX 中正確運作的路徑和檔案名（區分大小寫）。 Win32 作業系統中的檔案配置表 (FAT) 檔案系統不區分大小寫。 NTFS 檔案系統會保留目錄清單的大小寫，但會忽略檔案搜尋和其他系統作業中的大小寫。

> [!NOTE]
>  在此版本的 Visual C++ 中，我們已從函式描述中移除 UNIX 相容性資訊。

## <a name="see-also"></a>另請參閱

[相容性](../c-runtime-library/compatibility.md)
