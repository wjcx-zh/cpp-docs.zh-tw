---
title: /ERRORREPORT (editbin.exe)
description: Microsoft EDITBIN utility/ERRORREPORT 命令列選項的參考。
ms.date: 02/09/2020
f1_keywords:
- /ERRORREPORT
helpviewer_keywords:
- -ERRORREPORT editbin option
- ERRORREPORT editbin option
- /ERRORREPORT editbin option
ms.assetid: eca66ac3-b754-4bd7-9dd4-e04fc79a71b6
ms.openlocfilehash: 6c2ec8b6cda7b794114ed38cfb72b885bf2e38a1
ms.sourcegitcommit: 8414cd91297dea88c480e208c7b5301db9972f19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2020
ms.locfileid: "77257585"
---
# <a name="errorreport-editbinexe"></a>/ERRORREPORT (editbin.exe)

> [!NOTE]
> /ERRORREPORT 選項已被取代。 從 Windows Vista 開始，錯誤報表是由[Windows 錯誤報告（WER）](/windows/win32/wer/windows-error-reporting)設定所控制。

## <a name="syntax"></a>語法

> **/ERRORREPORT** \[ **NONE** \|**提示**字元 \|**佇列**\|**傳送**]

## <a name="remarks"></a>備註

Windows 錯誤報告的服務設定會覆寫 **/ERRORREPORT**引數。 如果 Windows 錯誤報告啟用報告功能，EDITBIN 會自動將內部錯誤的報告傳送給 Microsoft。 如果 Windows 錯誤報告停用，則不會傳送任何報表。

## <a name="see-also"></a>另請參閱

[EDITBIN 選項](editbin-options.md)
