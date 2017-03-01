---
title: "ATL OLE DB 提供者精靈 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- vc.codewiz.class.atl.provider.overview
dev_langs:
- C++
helpviewer_keywords:
- ATL OLE DB Provider Wizard
- ATL projects, adding ATL OLE DB providers
ms.assetid: cf91ba78-01d1-4d12-b673-e95d96bfbebe
caps.latest.revision: 13
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: aa6eb732c15fa2bc392296de1cc035cff1e0dcee
ms.lasthandoff: 02/24/2017

---
# <a name="atl-ole-db-provider-wizard"></a>ATL OLE DB 提供者精靈
此精靈會建立撰寫 OLE DB 提供者的類別。  
  
## <a name="remarks"></a>備註  
 開頭為[!INCLUDE[vs_orcas_long](../../atl/reference/includes/vs_orcas_long_md.md)]，此精靈所產生的註冊指令碼將會註冊 COM 元件在**HKEY_CURRENT_USER**而不是**HKEY_LOCAL_MACHINE**。 若要修改此行為，請設定**註冊元件的所有使用者**ATL 精靈的選項。  
  
 下表說明 ATL OLE DB 提供者精靈的選項︰  
  
 **簡短名稱**  
 輸入要建立的提供者的簡短名稱。 在精靈中的其他編輯方塊便會自動填入您在此處輸入為基礎。 如果您想要您可以編輯其他名稱方塊。  
  
 **Coclass**  
 Coclass 的名稱。 ProgID 的名稱會變更為符合此名稱。  
  
 **使用屬性**  
 此選項指定精靈是否將建立使用屬性或樣板宣告的提供者類別。 當您選取此選項時，精靈會使用屬性，而不是樣板宣告 （如果您建立屬性化的專案，這是預設選項）。 當您清除此選項時，精靈會使用樣板宣告，而不是屬性 （如果您建立非屬性化專案，這是預設選項）。  
  
 如果您選取此選項，當您建立非屬性化專案時，精靈會警告您專案將會轉換成屬性化專案，並詢問您是否要繼續進行。  
  
 **ProgID**  
 ProgID 或程式設計識別項，為您的應用程式可以使用，而不是 GUID 字串。 ProgID 的名稱的格式*Projectname*。*Coclassname*。  
  
 **版本**  
 您的提供者版本號碼。 預設為 1。  
  
 **資料來源類別**  
 格式為 C 的資料來源類別名稱`Shortname`來源。  
  
 **資料來源的.h 檔案**  
 資料來源類別標頭檔。 您可以編輯此檔案的名稱，或選取現有的標頭檔。  
  
 **工作階段類別**  
 工作階段類別，格式為 C 的名稱`Shortname`工作階段。  
  
 **工作階段的.h 檔案**  
 工作階段類別的標頭檔。 您可以編輯此檔案的名稱，或選取現有的標頭檔。  
  
 **命令類別**  
 命令類別，格式為 C 的名稱`Shortname`命令。  
  
 **命令.h 檔案**  
 命令類別標頭檔。 這個名稱不能編輯，取決於資料列集標頭檔的名稱。  
  
 **資料列集類別**  
 名稱的資料列集類別，格式為 C`Shortname`資料列集。  
  
 **資料列集的.h 檔案**  
 資料列集類別的標頭檔。 您可以編輯此檔案的名稱，或選取現有的標頭檔。  
  
 **.Cpp 檔案中資料列集**  
 提供者的實作檔案。 您可以編輯此檔案的名稱，或選取現有的實作檔。  
  
## <a name="see-also"></a>另請參閱  
 [ATL OLE DB 提供者](../../atl/reference/adding-an-atl-ole-db-provider.md)


