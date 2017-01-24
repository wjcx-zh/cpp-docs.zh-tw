---
title: "MFC ActiveX 控制項：序列化 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "_wVerMinor"
  - "DoPropExchange"
  - "_wVerMajor"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "DoPropExchange 方法"
  - "ExchangeVersion 方法"
  - "GetVersion 方法"
  - "MFC ActiveX 控制項, 序列化"
  - "MFC ActiveX 控制項, 版本支援"
  - "版本控制 ActiveX 控制項"
  - "wVerMajor 全域常數"
  - "wVerMinor 全域常數"
ms.assetid: 9d57c290-dd8c-4853-b552-6f17f15ebedd
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# MFC ActiveX 控制項：序列化
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本文將討論如何序列化 ActiveX 控制項。  還原序列化是讀取或寫入處理序對一個持續性儲存體儲存媒體，例如磁碟檔案。  Microsoft Foundation Class \(MFC\) 程式庫提供在類別 `CObject`序列化的內建支援。  `COleControl` 為 ActiveX 控制項支援此使用屬性交換機制。  
  
 ActiveX 控制項的序列化藉由覆寫 [COleControl::DoPropExchange](../Topic/COleControl::DoPropExchange.md)實作。  這個函式，在控制項物件的載入和儲存期間，儲存所有屬性實作與 10% 成員變數或 10% 成員變數的變更通知。  
  
 下列主題包含主題與序列化 ActiveX 控制項有關聯:  
  
-   實作 `DoPropExchange` 函式可以序列化您的控制項物件。  
  
-   [自訂序列化程序](#_core_customizing_the_default_behavior_of_dopropexchange)  
  
-   [實作版本支援](#_core_implementing_version_support)  
  
##  <a name="_core_implementing_the_dopropexchange_function"></a> 實作DoPropExchange函式  
 當您使用 ActiveX 控制項精靈產生控制項專案時，有幾個預設處理常式函式會自動加入至控制項的類別，包括 [COleControl::DoPropExchange](../Topic/COleControl::DoPropExchange.md)的預設實作。  下列範例顯示程式碼加入至類別建立 ActiveX 控制項精靈:  
  
 [!code-cpp[NVC_MFC_AxUI#43](../mfc/codesnippet/CPP/mfc-activex-controls-serializing_1.cpp)]  
  
 如果您想設定屬性，將會修改 `DoPropExchange` 到屬性切換函式。  下列範例示範自訂布林值 CircleShape 屬性的序列化， CircleShape 屬性有預設值 **TRUE**:  
  
 [!code-cpp[NVC_MFC_AxSer#1](../mfc/codesnippet/CPP/mfc-activex-controls-serializing_2.cpp)]  
[!code-cpp[NVC_MFC_AxSer#2](../mfc/codesnippet/CPP/mfc-activex-controls-serializing_3.cpp)]  
  
 下表列出您可用來控制序列化的屬性可能的屬性交換函式:  
  
|屬性切換函式|用途|  
|------------|--------|  
|**PX\_Blob\( \)**|序列化型別二進位大型物件 \(BLOB\) \(BLOB\) 資料屬性。|  
|**PX\_Bool\( \)**|序列化型別布林屬性。|  
|**PX\_Color\( \)**|序列化型別色彩屬性。|  
|**PX\_Currency\( \)**|序列化型別 **CY** \(貨幣\) 屬性。|  
|**PX\_Double\( \)**|序列化型別 **double** 屬性。|  
|**PX\_Font\( \)**|取得字型的屬性。|  
|**PX\_Float\( \)**|序列化型別 **float** 屬性。|  
|**PX\_IUnknown\( \)**|將 `LPUNKNOWN`型別的屬性。|  
|**PX\_Long\( \)**|序列化型別 **long** 屬性。|  
|**PX\_Picture\( \)**|序列化型別圖片屬性。|  
|**PX\_Short\( \)**|序列化型別 **short** 屬性。|  
|**PX\_String\( \)**|將 `CString` 型別的屬性。|  
|**PX\_ULong\( \)**|序列化型別 **ULONG** 屬性。|  
|**PX\_UShort\( \)**|序列化型別 **USHORT** 屬性。|  
  
 如需這些屬性切換函式的詳細資訊，請參閱《 *MFC 參考》中的*[OLE automation 控制項繼續](../mfc/reference/persistence-of-ole-controls.md) 。  
  
##  <a name="_core_customizing_the_default_behavior_of_dopropexchange"></a> 自訂 DoPropExchange 預設行為。  
 **DoPropertyExchange** 的預設實作 \(如上一個主題所示\) 呼叫基底類別的 `COleControl`。  這個序列化 `COleControl`自動支援的屬性集，則將只會顯示控制項的自訂屬性使用更多儲存空間。  移除這個呼叫可以讓您的物件序列化您認為重要的那些屬性。  所有共用屬性陳述控制項實作不會序列化，當儲存或載入控制項中物件時，除非您明確將 **PX\_** 呼叫它們。  
  
##  <a name="_core_implementing_version_support"></a> 實作版本支援  
 版支援啟用已修改的 ActiveX 控制項加入新的保存屬性和仍然可以偵測和裝載控制項的舊版建立的這個持續性狀態。  做為其持續性資料的一部分，要讓控制項的版本，請在控制項的 `DoPropExchange` 函式中的 [COleControl::ExchangeVersion](../Topic/COleControl::ExchangeVersion.md) 。  如果 ActiveX 控制項會自動插入，這個呼叫使用 ActiveX 控制項精靈。  它支援版本，如果不需要，可以移除。  不過，在控制項大小的成本為版本支援提供的彈性非常小 \(4 位元組\)。  
  
 如果控制項未建立 ActiveX 控制項精靈，請將呼叫加入至 `COleControl::ExchangeVersion` 將下行程式碼插入您的 `DoPropExchange` 函式的開頭 \(在呼叫 `COleControl::DoPropExchange`之前\):  
  
 [!code-cpp[NVC_MFC_AxSer#1](../mfc/codesnippet/CPP/mfc-activex-controls-serializing_2.cpp)]  
[!code-cpp[NVC_MFC_AxSer#3](../mfc/codesnippet/CPP/mfc-activex-controls-serializing_4.cpp)]  
  
 您可以使用任何 `DWORD` 做為版本號碼。  ActiveX 控制項精靈所產生的專案 **\_wVerMinor** 和 **\_wVerMajor** 做為預設值。  這些是專案的 ActiveX 控制項類別的實作檔中定義的全域常數。  在 `DoPropExchange` 函式中的其餘部分，您可以隨時呼叫 [CPropExchange::GetVersion](../Topic/CPropExchange::GetVersion.md) 擷取您儲存或擷取的版本。  
  
 在下列範例中，這個版本範例控制項 1 只有一個 ReleaseDate」屬性。  版本 2 會加入「OriginalDate」屬性。  如果控制項指示從舊版本載入持續性狀態，它使用新屬性的成員變數設定為預設值。  
  
 [!code-cpp[NVC_MFC_AxSer#4](../mfc/codesnippet/CPP/mfc-activex-controls-serializing_5.cpp)]  
[!code-cpp[NVC_MFC_AxSer#3](../mfc/codesnippet/CPP/mfc-activex-controls-serializing_4.cpp)]  
  
 根據預設，控制項「轉換成」舊資料為最新的格式。  例如，如果控制項的版本 2 x 1 版保存的載入資料，當他再被儲存時，它會寫入 2 版格式時。  如果您要控制儲存格式的資料最後讀取，請將 **FALSE** 當做第三個參數，當呼叫 `ExchangeVersion`時。  預設為第三個參數是選擇性的和是 **TRUE** 。  
  
## 請參閱  
 [MFC ActiveX 控制項](../mfc/mfc-activex-controls.md)