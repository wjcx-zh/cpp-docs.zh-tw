---
title: 複製來源專案屬性 (Linux C++) | Microsoft Docs
ms.custom: ''
ms.date: 9/26/2017
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: Linux
ms.topic: conceptual
ms.assetid: 1a44230d-5dd8-4d33-93b4-e77e03e00150
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- linux
ms.openlocfilehash: d13bc7c129696e2b7251ccb23b68338956864321
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="copy-sources-project-properties-linux-c"></a>複製來源專案屬性 (Linux C++)

此屬性頁面上設定的屬性，會套用至專案中的所有檔案，但已設定檔案層級屬性的專案除外。

屬性 | 描述
--- | ---
要複製的來源 | 指定要複製到遠端系統的來源。 變更此清單可能會造成遠端系統上作為檔案複製目標的目錄結構變更，或到受影響。
複製來源 | 指定是否要將來源複製到遠端系統。
要複製的其他來源 | 指定要複製到遠端系統的其他來源。 您也可以使用類似如下的語法，將清單提供為本機到遠端的對應配對：fulllocalpath1:=fullremotepath1;fulllocalpath2:=fullremotepath2，如此會將本機檔案複製到遠端系統上指定的遠端位置。
