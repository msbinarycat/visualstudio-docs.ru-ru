---
title: IDebugProgramEx2::Attach | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramEx2::Attach
helpviewer_keywords:
- IDebugProgramEx2::Attach
ms.assetid: 33b22b2f-431e-4205-9441-d28a9c928c97
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: db27f29b37480081d29e452d74a6da0c5cea59a6
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66325187"
---
# <a name="idebugprogramex2attach"></a>IDebugProgramEx2::Attach
Присоединиться к программе сеанса.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT Attach( 
   IDebugEventCallback2* pCallback,
   DWORD                 dwReason,
   IDebugSession2*       pSession
);
```

```csharp
int Attach( 
   IDebugEventCallback2 pCallback,
   uint                 dwReason,
   IDebugSession2       pSession
);
```

## <a name="parameters"></a>Параметры
`pCallback`\
[in] [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) объект, который представляет вложенные отладчик отправляет события в функцию обратного вызова.

`dwReason`\
[in] Значение из [ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md) перечисление, описывающее причину для операции присоединения.

`pSession`\
[in] Значение, уникально идентифицирующий сеанс, который присоединяется к программе.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки. Этот метод должен возвращать `E_ATTACH_DEBUGGER_ALREADY_ATTACHED` Если программа уже подключен.

## <a name="remarks"></a>Примечания
 Порт, в которой находится программа может использовать значение в `pSession` для определения, какой сеанс пытается присоединить к программе. Например если порт допускает только один отладку для присоединения к процессу одновременно, порт можно определить сеанс уже назначена ли другие программы, в процессе.

> [!NOTE]
> Переданный интерфейс `pSession` следует рассматривать только как файл cookie, значение, однозначно определяющий диспетчер отладки сеансов, присоединить к этой программе; ни один из методов предоставленного интерфейса являются рабочими.

## <a name="see-also"></a>См. также
- [IDebugProgramEx2](../../../extensibility/debugger/reference/idebugprogramex2.md)