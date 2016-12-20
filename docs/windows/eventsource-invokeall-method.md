---
title: "EventSource::InvokeAll 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "event/Microsoft::WRL::EventSource::InvokeAll"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "InvokeAll 方法"
ms.assetid: 1506618f-0421-4428-a4d0-4ea2b10a3bf6
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# EventSource::InvokeAll 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

目前相關聯的每個事件處理常式會呼叫 [EventSource](../windows/eventsource-class.md) 物件使用指定的引數型別和引數。  
  
## <a name="syntax"></a>語法  
  
```  
void InvokeAll();  
template <  
   typename T0  
>  
void InvokeAll(  
   T0arg0  
);  
template <  
   typename T0,  
   typename T1  
>  
void InvokeAll(  
   T0arg0,  
   T1arg1  
);  
template <  
   typename T0,  
   typename T1,  
   typename T2  
>  
void InvokeAll(  
   T0arg0,  
   T1arg1,  
   T2arg2  
);  
template <  
   typename T0,  
   typename T1,  
   typename T2,  
   typename T3  
>  
void InvokeAll(  
   T0arg0,  
   T1arg1,  
   T2arg2,  
   T3arg3  
);  
template <  
   typename T0,  
   typename T1,  
   typename T2,  
   typename T3,  
   typename T4  
>  
void InvokeAll(  
   T0arg0,  
   T1arg1,  
   T2arg2,  
   T3arg3,  
   T4arg4  
);  
template <  
   typename T0,  
   typename T1,  
   typename T2,  
   typename T3,  
   typename T4,  
   typename T5  
>  
void InvokeAll(  
   T0arg0,  
   T1arg1,  
   T2arg2,  
   T3arg3,  
   T4arg4,  
   T5arg5  
);  
template <  
   typename T0,  
   typename T1,  
   typename T2,  
   typename T3,  
   typename T4,  
   typename T5,  
   typename T6  
>  
void InvokeAll(  
   T0arg0,  
   T1arg1,  
   T2arg2,  
   T3arg3,  
   T4arg4,  
   T5arg5,  
   T6arg6  
);  
template <  
   typename T0,  
   typename T1,  
   typename T2,  
   typename T3,  
   typename T4,  
   typename T5,  
   typename T6,  
   typename T7  
>  
void InvokeAll(  
   T0arg0,  
   T1arg1,  
   T2arg2,  
   T3arg3,  
   T4arg4,  
   T5arg5,  
   T6arg6,  
   T7arg7  
);  
template <  
   typename T0,  
   typename T1,  
   typename T2,  
   typename T3,  
   typename T4,  
   typename T5,  
   typename T6,  
   typename T7,  
   typename T8  
>  
void InvokeAll(  
   T0arg0,  
   T1arg1,  
   T2arg2,  
   T3arg3,  
   T4arg4,  
   T5arg5,  
   T6arg6,  
   T7arg7,  
   T8arg8  
);  
template <  
   typename T0,  
   typename T1,  
   typename T2,  
   typename T3,  
   typename T4,  
   typename T5,  
   typename T6,  
   typename T7,  
   typename T8,  
   typename T9  
>  
void InvokeAll(  
   T0arg0,  
   T1arg1,  
   T2arg2,  
   T3arg3,  
   T4arg4,  
   T5arg5,  
   T6arg6,  
   T7arg7,  
   T8arg8,  
   T9arg9  
);  
```  
  
#### <a name="parameters"></a>參數  
 `T0`  
 預備事件處理常式的引數的型別。  
  
 `T1`  
 第一個事件處理常式引數型別。  
  
 `T2`  
 第二個事件處理常式引數的型別。  
  
 `T3`  
 第三個事件處理常式引數的型別。  
  
 `T4`  
 第四個事件處理常式引數的型別。  
  
 `T5`  
 第五個事件處理常式引數的型別。  
  
 `T6`  
 第六個事件處理常式引數的型別。  
  
 `T7`  
 第七個事件處理常式引數的型別。  
  
 `T8`  
 八個事件處理常式引數型別。  
  
 `T9`  
 第九個事件處理常式引數的型別。  
  
 `arg0`  
 預備事件處理常式引數。  
  
 `arg1`  
 第一個事件處理常式引數。  
  
 `arg2`  
 第二個事件處理常式引數。  
  
 `arg3`  
 第三個事件處理常式引數。  
  
 `arg4`  
 第四個事件處理常式引數。  
  
 `arg5`  
 第五個事件處理常式引數。  
  
 `arg6`  
 第六個事件處理常式引數。  
  
 `arg7`  
 第七個事件處理常式引數。  
  
 `arg8`  
 兩個事件處理常式引數。  
  
 `arg9`  
 第九個事件處理常式引數。  
  
## <a name="requirements"></a>需求  
 **標頭︰** event.h  
  
 **命名空間：** Microsoft::WRL
 
 ## <a name="see-also"></a>另請參閱
 [EventSource 類別](../windows/eventsource-class.md)