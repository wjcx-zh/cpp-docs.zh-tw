---
title: ATL OLE DB 提供者精靈 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- vc.codewiz.class.atl.provider.overview
dev_langs:
- C++
helpviewer_keywords:
- ATL OLE DB Provider Wizard
- ATL projects, adding ATL OLE DB providers
ms.assetid: cf91ba78-01d1-4d12-b673-e95d96bfbebe
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 827b46de299341f23d0b799a5ed44b8923bbc182
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32357476"
---
# <a name="atl-ole-db-provider-wizard"></a>ATL OLE DB 提供者精靈
此精靈會建立撰寫 OLE DB 提供者的類別。  
  
## <a name="remarks"></a>備註  
 從 Visual Studio 2008 開始，此精靈所產生註冊指令碼會登錄其下的 COM 元件**HKEY_CURRENT_USER**而不是**HKEY_LOCAL_MACHINE**。 若要修改這個行為，請設定**註冊元件的所有使用者**ATL 精靈的選項。  
  
 下表描述 ATL OLE DB 提供者精靈的選項：  
  
 **簡短名稱**  
 輸入要建立的提供者的簡短名稱。 自動填入精靈中的其他編輯方塊，將會根據您在此處輸入。 如果您想要您可以編輯其他名稱方塊。  
  
 **coclass**  
 Coclass 的名稱。 ProgID 的名稱會變更為符合此名稱。  
  
 **使用屬性**  
 這個選項會指定精靈是否將建立使用屬性或樣板宣告提供者類別。 當您選取此選項時，精靈會使用屬性代替樣板宣告 （如果您建立的屬性化的專案，這是預設選項）。 當您清除此選項時，精靈會使用樣板宣告，而非屬性 （如果您建立非屬性化專案，這是預設選項）。  
  
 如果您選取此選項，當您建立的非屬性化專案時，精靈會警告您專案將轉換為屬性化專案，並詢問您是否要繼續進行。  
  
 **ProgID**  
 ProgID 或程式設計識別碼，為您的應用程式可以使用而不是 GUID 的文字字串。 ProgID 的名稱中有表單*為 Projectname.Coclassname*。  
  
 **版本**  
 您的提供者版本號碼。 預設為 1。  
  
 **資料來源類別**  
 格式為 C 的資料來源類別名稱*Shortname*來源。  
  
 **資料來源的.h 檔案**  
 資料來源類別標頭檔。 您可以編輯此檔案的名稱，或選取現有的標頭檔。  
  
 **工作階段類別**  
 工作階段類別，格式為 C 的名稱*Shortname*工作階段。  
  
 **工作階段的.h 檔案**  
 工作階段類別的標頭檔。 您可以編輯此檔案的名稱，或選取現有的標頭檔。  
  
 **命令類別**  
 命令類別，格式為 C 的名稱*Shortname*命令。  
  
 **命令的.h 檔案**  
 命令類別標頭檔。 這個名稱無法加以編輯，取決於資料列集標頭檔的名稱。  
  
 **資料列集類別**  
 資料列集類別，格式為 C 的名稱*Shortname*資料列集。  
  
 **資料列集的.h 檔案**  
 資料列集類別的標頭檔。 您可以編輯此檔案的名稱，或選取現有的標頭檔。  
  
 **.Cpp 檔案中資料列集**  
 提供者的實作檔。 您可以編輯此檔案的名稱，或選取現有的實作檔。  
  
## <a name="see-also"></a>另請參閱  
 [ATL OLE DB 提供者](../../atl/reference/adding-an-atl-ole-db-provider.md)

