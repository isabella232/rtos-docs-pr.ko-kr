---
title: USBX 호스트 클래스 API
description: 이 장에서는 USBX 호스트 클래스의 노출된 모든 API에 대해 설명합니다.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 28e733e37b06da7053f238e23e2b8b8046df2dd9940e50cd0321ccf15c27ec47
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/07/2021
ms.locfileid: "116802110"
---
# <a name="chapter-2-usbx-host-classes-api"></a>2장: USBX 호스트 클래스 API

이 장에서는 USBX 호스트 클래스의 노출된 모든 API에 대해 설명합니다. 다음과 같은 각 클래스용 API에 대해 자세히 설명합니다.

- Printer 클래스
- Audio 클래스
- Asix 클래스
- Pima/PTP 클래스
- Prolific 클래스
- Generic Serial 클래스

## <a name="ux_host_class_printer_read"></a>ux_host_class_printer_read

프린터 인터페이스에서 읽습니다.

### <a name="prototype"></a>프로토타입

```C
UINT ux_host_class_printer_read(
    UX_HOST_CLASS_PRINTER *printer,
    UCHAR *data_pointer,
    ULONG requested_length,
    ULONG *actual_length)
```

### <a name="description"></a>Description

이 함수는 프린터 인터페이스에서 읽습니다. 호출이 차단되고 오류가 있거나 전송이 완료된 경우에만 반환합니다. 읽기는 양방향 프린터에서만 허용됩니다.

### <a name="parameters"></a>매개 변수

- **printer**: 프린터 클래스 인스턴스에 대한 포인터입니다.
- **data_pointer**: 데이터 페이로드의 버퍼 주소에 대한 포인터입니다.
- **requested_length**: 수신될 길이입니다.
- **actual_length**: 실제로 수신된 길이입니다.

### <a name="return-value"></a>반환 값

- **UX_SUCCESS**: (0x00) 데이터 전송이 완료되었습니다.
- **UX_FUNCTION_NOT_SUPPORTED**: (0x54) 프린터가 양방향이 아니기 때문에 지원되지 않습니다.
- **UX_TRANSFER_TIMEOUT**: (0x5c) 전송 시간 제한을 초과했습니다. 읽기가 완료되지 않았습니다.

### <a name="example"></a>예제

```C
UINT status;

/* The following example illustrates this service. */
status = ux_host_class_printer_read(printer, data_pointer, requested_length, &actual_length);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_printer_write"></a>ux_host_class_printer_write

프린터 인터페이스에 씁니다.

### <a name="prototype"></a>프로토타입

```C
UINT ux_host_class_printer_write(
    UX_HOST_CLASS_PRINTER *printer,
    UCHAR *data_pointer,  
    ULONG requested_length,
    ULONG *actual_length)
```

### <a name="description"></a>Description

이 함수는 프린터 인터페이스에 씁니다. 호출이 차단되고 오류가 있거나 전송이 완료된 경우에만 반환합니다.

### <a name="parameters"></a>매개 변수

- **printer**: 프린터 클래스 인스턴스에 대한 포인터입니다.
- **data_pointer**: 데이터 페이로드의 버퍼 주소에 대한 포인터입니다.
- **requested_length**: 전송될 길이입니다.
- **actual_length**: 실제로 전송된 길이입니다.

### <a name="return-value"></a>반환 값

- **UX_SUCCESS**: (0x00) 데이터 전송이 완료되었습니다.
- **UX_TRANSFER_TIMEOUT**: (0x5c) 전송 시간 제한을 초과했습니다. 쓰기가 완료되지 않았습니다.

### <a name="example"></a>예제

```C
UINT status;

/* The following example illustrates this service. */
status = ux_host_class_printer_write(printer, data_pointer, requested_length, &actual_length);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_printer_soft_reset"></a>ux_host_class_printer_soft_reset

프린터에 대한 소프트 초기화를 수행합니다.

### <a name="prototype"></a>프로토타입

```C
UINT ux_host_class_printer_soft_reset(UX_HOST_CLASS_PRINTER *printer)
```

### <a name="description"></a>Description

이 함수는 프린터에 대한 소프트 초기화를 수행합니다.

### <a name="input-parameter"></a>입력 매개 변수

- **printer**: 프린터 클래스 인스턴스에 대한 포인터입니다.

### <a name="return-value"></a>반환 값

- **UX_SUCCESS**: (0x00) 초기화가 완료되었습니다.
- **UX_TRANSFER_TIMEOUT**: (0x5c) 전송 시간 제한을 초과했습니다. 초기화가 완료되지 않았습니다.

### <a name="example"></a>예제

```C
UINT status;

/* The following example illustrates this service. */
status = ux_host_class_printer_soft_reset(printer);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_printer_status_get"></a>ux_host_class_printer_status_get

프린터 상태 가져오기

### <a name="prototype"></a>프로토타입

```C
UINT ux_host_class_printer_status_get( 
    UX_HOST_CLASS_PRINTER *printer,
    ULONG *printer_status)
```

### <a name="description"></a>Description

이 함수는 프린터 상태를 가져옵니다. 프린터 상태는 LPT 상태(1284 표준)와 유사합니다.

### <a name="parameters"></a>매개 변수

- **printer**: 프린터 클래스 인스턴스에 대한 포인터입니다.
- **printer_status**: 반환될 상태의 주소입니다.

### <a name="return-value"></a>반환 값

- **UX_SUCCESS**(0x00): 초기화가 완료되었습니다.
- **UX_MEMORY_INSUFFICIENT**: (0x12) 메모리가 부족하여 작업을 수행할 수 없습니다.
- **UX_TRANSFER_TIMEOUT**: (0x5c) 전송 시간 제한을 초과했습니다. 초기화가 완료되지 않았습니다.

### <a name="example"></a>예제

```C
UINT status;

/* The following example illustrates this service. */
status = ux_host_class_printer_status_get(printer, printer_status);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_printer_device_id_get"></a>ux_host_class_printer_device_id_get

프린터 디바이스 ID를 가져옵니다.

### <a name="prototype"></a>프로토타입

```C
UINT ux_host_class_printer_device_id_get( 
    UX_HOST_CLASS_PRINTER *printer,
    UCHAR *descriptor_buffer, 
    ULONG length)
```

### <a name="description"></a>Description

이 함수는 프린터 IEEE 1284 디바이스 ID 문자열(Big Endian 형식의 처음 2바이트 길이 포함)을 가져옵니다.

### <a name="parameters"></a>매개 변수

- **printer**: 프린터 클래스 인스턴스에 대한 포인터입니다.
- **descriptor_buffer**: IEEE 1284 디바이스 ID 문자열(BE 형식으로 처음 2바이트의 길이 포함)을 채우는 버퍼에 대한 포인터입니다. 
- **length**: 버퍼의 길이(바이트)입니다.

### <a name="return-value"></a>반환 값

- **UX_SUCCESS** (0x00): 작업이 성공적으로 수행되었습니다.
- **UX_MEMORY_INSUFFICIENT**: (0x12) 메모리가 부족하여 작업을 수행할 수 없습니다.
- **UX_TRANSFER_TIMEOUT**: (0x5c) 전송 시간 제한을 초과했습니다. 요청이 완료되지 않았습니다.
- **UX_TRANSFER_NOT_READY**: (0x25) 디바이스 상태가 잘못되었습니다. ATTACHED, ADDRESSED 또는 CONFIGURED여야 합니다.
- **UX_TRANSFER_STALL**: (0x21) 전송이 중단되었습니다.
- **TX_WAIT_ABORTED** (0x1A) 일시 중단이 다른 스레드, 타이머 또는 ISR에 의해 취소되었습니다.
- **TX_SEMAPHORE_ERROR**(0x0C) 잘못된 가산 세마포 포인터입니다.
- **TX_WAIT_ERROR** (0x04) 비스레드의 호출에서 TX_NO_WAIT 이외의 대기 옵션이 지정되었습니다.

### <a name="example"></a>예제

```C
UINT status;

/* The following example illustrates this service. */
status = ux_host_class_printer_device_id_get(printer, descriptor_buffer, length);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_audio_read"></a>ux_host_class_audio_read

오디오 인터페이스에서 읽습니다.

### <a name="prototype"></a>프로토타입

```C
UINT ux_host_class_audio_read(
    UX_HOST_CLASS_AUDIO *audio,
    UX_HOST_CLASS_AUDIO_TRANSFER_REQUEST
    *audio_transfer_request)
```

### <a name="description"></a>Description

이 함수는 오디오 인터페이스에서 읽습니다. 이 호출은 차단되지 않습니다. 애플리케이션에서 오디오 스트리밍 인터페이스를 위해 적절한 대체 설정이 선택되어 있는지 확인해야 합니다.

### <a name="parameters"></a>매개 변수

- **audio**: 오디오 클래스 인스턴스에 대한 포인터입니다.
- **audio_transfer_request**: 오디오 전송 구조에 대한 포인터입니다.

### <a name="return-value"></a>반환 값

- **UX_SUCCESS**: (0x00) 데이터 전송이 완료되었습니다.
- **UX_FUNCTION_NOT_SUPPORTED**" (0x54) 함수는 지원되지 않습니다.

### <a name="example"></a>예제

```C
/* The following example reads from the audio interface. */

audio_transfer_request.ux_host_class_audio_transfer_request_completion_function = tx_audio_transfer_completion_function;
audio_transfer_request.ux_host_class_audio_transfer_request_class_instance = audio;
audio_transfer_request.ux_host_class_audio_transfer_request_next_audio_audio_transfer_request = UX_NULL;
audio_transfer_request.ux_host_class_audio_transfer_request_data_pointer = audio_buffer;
audio_transfer_request.ux_host_class_audio_transfer_request_requested_length = requested_length;
audio_transfer_request.ux_host_class_audio_transfer_request_packet_length = AUDIO_FRAME_LENGTH;

status = ux_host_class_audio_read(audio, audio_transfer_request);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_audio_write"></a>ux_host_class_audio_write

오디오 인터페이스에 씁니다.

### <a name="prototype"></a>프로토타입

```C
UINT ux_host_class_audio_write(
    UX_HOST_CLASS_AUDIO *audio,
    UX_HOST_CLASS_AUDIO_TRANSFER_REQUEST *audio_transfer_request)
```

### <a name="description"></a>Description

이 함수는 오디오 인터페이스에 씁니다. 이 호출은 차단되지 않습니다. 애플리케이션에서 오디오 스트리밍 인터페이스를 위해 적절한 대체 설정이 선택되어 있는지 확인해야 합니다.

### <a name="parameters"></a>매개 변수

- **audio**: 오디오 클래스 인스턴스에 대한 포인터입니다.
- **audio_transfer_request**: 오디오 전송 구조에 대한 포인터입니다.

### <a name="return-value"></a>반환 값

- **UX_SUCCESS**: (0x00) 데이터 전송이 완료되었습니다.
- **UX_FUNCTION_NOT_SUPPORTED**: (0x54) 함수는 지원되지 않습니다.
- **ux_host_CLASS_AUDIO_WRONG_INTERFACE**: (0x81) 인터페이스가 잘못되었습니다.

### <a name="example"></a>예제

```C
UINT status;

/* The following example writes to the audio interface */

audio_transfer_request.ux_host_class_audio_transfer_request_completion_function = tx_audio_transfer_completion_function;
audio_transfer_request.ux_host_class_audio_transfer_request_class_instance = audio;
audio_transfer_request.ux_host_class_audio_transfer_request_next_audio_audio_transfer_request = UX_NULL;
audio_transfer_request.ux_host_class_audio_transfer_request_data_pointer = audio_buffer;
audio_transfer_request.ux_host_class_audio_transfer_request_requested_length = requested_length;
audio_transfer_request.ux_host_class_audio_transfer_request_packet_length = AUDIO_FRAME_LENGTH;
status = ux_host_class_audio_write(audio, audio_transfer_request);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_audio_control_get"></a>ux_host_class_audio_control_get

오디오 컨트롤 인터페이스에서 특정 컨트롤을 가져옵니다.

### <a name="prototype"></a>프로토타입

```C
UINT ux_host_class_audio_control_get(
    UX_HOST_CLASS_AUDIO *audio,
    UX_HOST_CLASS_AUDIO_CONTROL *audio_control)
```

### <a name="description"></a>Description

이 함수는 오디오 컨트롤 인터페이스에서 특정 컨트롤을 읽습니다.

### <a name="parameters"></a>매개 변수

- **audio**: 오디오 클래스 인스턴스에 대한 포인터입니다.
- **audio_control**: 오디오 컨트롤 구조에 대한 포인터입니다.

### <a name="return-value"></a>반환 값

- **UX_SUCCESS**: (0x00) 데이터 전송이 완료되었습니다.
- **UX_FUNCTION_NOT_SUPPORTED**: (0x54) 함수는 지원되지 않습니다.
- **UX_HOST_CLASS_AUDIO_WRONG_INTERFACE**: (0x81) 인터페이스가 잘못되었습니다.

### <a name="example"></a>예제

```C
UINT status;

/* The following example reads the volume control from a stereo USB speaker. */

UX_HOST_CLASS_AUDIO_CONTROL audio_control;

audio_control.ux_host_class_audio_control_channel = 1;
audio_control.ux_host_class_audio_control = UX_HOST_CLASS_AUDIO_VOLUME_CONTROL;

status = ux_host_class_audio_control_get(audio, &audio_control);

/* If status equals UX_SUCCESS, the operation was successful. */

audio_control.ux_host_class_audio_control_channel = 2;
audio_control.ux_host_class_audio_control = UX_HOST_CLASS_AUDIO_VOLUME_CONTROL;

status = ux_host_class_audio_control_get(audio, &audio_control);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_audio_control_value_set"></a>ux_host_class_audio_control_value_set

특정 컨트롤을 오디오 컨트롤 인터페이스로 설정합니다.

### <a name="prototype"></a>프로토타입

```C
UINT ux_host_class_audio_control_value_set(
    UX_HOST_CLASS_AUDIO *audio,
    UX_HOST_CLASS_AUDIO_CONTROL *audio_control)
```

**설명**

이 함수는 특정 컨트롤을 오디오 컨트롤 인터페이스로 설정합니다.

### <a name="parameters"></a>매개 변수

- **audio**: 오디오 클래스 인스턴스에 대한 포인터입니다.
- **audio_control**: 오디오 컨트롤 구조에 대한 포인터입니다.

### <a name="return-value"></a>반환 값

- **UX_SUCCESS**: (0x00) 데이터 전송이 완료되었습니다.
- **UX_FUNCTION_NOT_SUPPORTED**: (0x54) 함수는 지원되지 않습니다.
- **UX_HOST_CLASS_AUDIO_WRONG_INTERFACE**: (0x81) 인터페이스가 잘못되었습니다.

### <a name="example"></a>예제

```C
/* The following example sets the volume control of a stereo USB speaker. */

UX_HOST_CLASS_AUDIO_CONTROL audio_control;

UINT status;

audio_control.ux_host_class_audio_control_channel = 1;
audio_control.ux_host_class_audio_control = UX_HOST_CLASS_AUDIO_VOLUME_CONTROL;
audio_control.ux_host_class_audio_control_cur = 0xf000;

status = ux_host_class_audio_control_value_set(audio, &audio_control);
/* If status equals UX_SUCCESS, the operation was successful. */

current_volume = audio_control.audio_control_cur;
audio_control.ux_host_class_audio_control_channel = 2;
audio_control.ux_host_class_audio_control = UX_HOST_CLASS_AUDIO_VOLUME_CONTROL;
audio_control.ux_host_class_audio_control_cur = 0xf000;

status = ux_host_class_audio_control_value_set(audio, &audio_control);
/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_audio_streaming_sampling_set"></a>ux_host_class_audio_streaming_sampling_set

오디오 스트리밍 인터페이스의 대체 설정 인터페이스를 설정합니다.

### <a name="prototype"></a>프로토타입

```C
UINT ux_host_class_audio_streaming_sampling_set
    (UX_HOST_CLASS_AUDIO *audio,
    UX_HOST_CLASS_AUDIO_SAMPLING *audio_sampling)
```

### <a name="description"></a>Description

이 함수는 특정 샘플링 구조에 따라 오디오 스트리밍 인터페이스의 대체 설정 인터페이스를 적절하게 설정합니다.

### <a name="parameters"></a>매개 변수

- **audio**: 오디오 클래스 인스턴스에 대한 포인터입니다.
- **audio_sampling**: 오디오 샘플링 구조에 대한 포인터입니다.

### <a name="return-value"></a>반환 값

- **UX_SUCCESS**: (0x00) 데이터 전송이 완료되었습니다.
- **UX_FUNCTION_NOT_SUPPORTED**: (0x54) 함수는 지원되지 않습니다.
- **UX_HOST_CLASS_AUDIO_WRONG_INTERFACE**: (0x81) 인터페이스가 잘못되었습니다.
- **UX_NO_ALTERNATE_SETTING**: (0x5e) 샘플링 값에 대한 대체 설정이 없습니다.

### <a name="example"></a>예제

```C
/* The following example sets the alternate setting interface of a stereo USB speaker. */

UX_HOST_CLASS_AUDIO_SAMPLING audio_sampling;

UINT status;

sampling.ux_host_class_audio_sampling_channels = 2;
sampling.ux_host_class_audio_sampling_frequency = AUDIO_FREQUENCY;
sampling. ux_host_class_audio_sampling_resolution = 16;

status = ux_host_class_audio_streaming_sampling_set(audio, &sampling);
/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_audio_streaming_sampling_get"></a>ux_host_class_audio_streaming_sampling_get

오디오 스트리밍 인터페이스에서 사용 가능한 샘플링 설정을 가져옵니다.

### <a name="prototype"></a>프로토타입

```C
UINT ux_host_class_audio_streaming_sampling_get(
    UX_HOST_CLASS_AUDIO *audio,
    UX_HOST_CLASS_AUDIO_SAMPLING_CHARACTERISTICS *audio_sampling)
```

### <a name="description"></a>Description

이 함수는 오디오 스트리밍 인터페이스의 각 대체 설정에서 사용할 수 있는 모든 샘플링 설정을 하나씩 가져옵니다. 함수를 처음 사용하는 경우 호출 구조 포인터의 모든 필드를 초기화해야 합니다. 이 함수는 대체 설정의 끝에 도달하지 않는 한 반환 시 스트리밍 값의 특정 세트를 반환합니다. 이 함수를 다시 사용하면 앞의 샘플링 값이 다음 샘플링 값을 찾는 데 사용됩니다.

### <a name="parameters"></a>매개 변수

- **audio**: 오디오 클래스 인스턴스에 대한 포인터입니다.
- **audio_sampling**: 오디오 샘플링 구조에 대한 포인터입니다.

### <a name="return-value"></a>반환 값

- **UX_SUCCESS**: (0x00) 데이터 전송이 완료되었습니다.
- **UX_FUNCTION_NOT_SUPPORTED**: (0x54) 함수는 지원되지 않습니다.
- **UX_HOST_CLASS_AUDIO_WRONG_INTERFACE**: (0x81) 인터페이스가 잘못되었습니다.
- **UX_NO_ALTERNATE_SETTING**: (0x5e) 샘플링 값에 대한 대체 설정이 없습니다.

### <a name="example"></a>예제

```C
/* The following example gets the sampling values for the first alternate setting interface of a stereo USB speaker. */

UX_HOST_CLASS_AUDIO_SAMPLING_CHARACTERISTICS audio_sampling;

UINT status;

sampling.ux_host_class_audio_sampling_channels=0;
sampling.ux_host_class_audio_sampling_frequency_low=0;
sampling.ux_host_class_audio_sampling_frequency_high=0;
sampling.ux_host_class_audio_sampling_resolution=0;

status = ux_host_class_audio_streaming_sampling_get(audio, &sampling);

/* If status equals UX_SUCCESS, the operation was successful and information could be displayed as follows:

printf("Number of channels %d, Resolution %d bits, frequency range %d-%d\n",
    sampling.audio_channels, sampling.audio_resolution,
    sampling.audio_frequency_low, sampling.audio_frequency_high);

*/
```

## <a name="ux_host_class_asix_read"></a>ux_host_class_asix_read

Asix 인터페이스에서 읽습니다.

### <a name="prototype"></a>프로토타입

```C
UINT ux_host_class_asix_read(
    UX_HOST_CLASS_ASIX *asix,
    UCHAR *data_pointer,
    ULONG requested_length,
    ULONG *actual_length)
```

### <a name="description"></a>Description

이 함수는 asix 인터페이스에서 읽습니다. 호출이 차단되고 오류가 있거나 전송이 완료된 경우에만 반환합니다.

### <a name="parameters"></a>매개 변수

- **asix**: asix 클래스 인스턴스에 대한 포인터입니다.
- **data_pointer**: 데이터 페이로드의 버퍼 주소에 대한 포인터입니다.
- **requested_length**: 수신될 길이입니다.
- **actual_length**: 실제로 수신된 길이입니다.

### <a name="return-value"></a>반환 값

- **UX_SUCCESS**: (0x00) 데이터 전송이 완료되었습니다.
- **UX_TRANSFER_TIMEOUT**: (0x5c) 전송 시간 제한을 초과했습니다. 읽기가 완료되지 않았습니다.

### <a name="example"></a>예제

```C
UINT status;

/* The following example illustrates this service. */

status = ux_host_class_asix_read(asix, data_pointer, requested_length, &actual_length);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_asix_write"></a>ux_host_class_asix_write

Asix 인터페이스에 씁니다.

### <a name="prototype"></a>프로토타입

```C
UINT ux_host_class_asix_write(
    VOID *asix_class,
    NX_PACKET *packet)
```

### <a name="description"></a>Description

이 함수는 asix 인터페이스에 씁니다. 이 호출은 차단되지 않습니다.

### <a name="parameters"></a>매개 변수

- **asix**: asix 클래스 인스턴스에 대한 포인터입니다.
- **패킷**: Netx 데이터 패킷입니다.

### <a name="return-value"></a>반환 값

- **UX_SUCCESS**: (0x00) 데이터 전송이 완료되었습니다.
- **UX_ERROR**: (0xFF) 전송을 요청할 수 없습니다.

### <a name="example"></a>예제

```C
UINT status;

/* The following example illustrates this service. */

status = ux_host_class_asix_write(asix, packet);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_pima_session_open"></a>ux_host_class_pima_session_open

개시 장치와 응답기 사이에서 세션을 엽니다.

### <a name="prototype"></a>프로토타입

```C
UINT ux_host_class_pima_session_open(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session)
```

### <a name="description"></a>Description

이 함수는 PIMA 개시 장치와 PIMA 응답기 사이에서 세션을 엽니다. 세션이 성공적으로 열리면 대부분의 PIMA 명령을 실행할 수 있습니다.

### <a name="parameters"></a>매개 변수

- **pima**: PIMA 클래스 인스턴스에 대한 포인터입니다.
- **pima_sessio**: PIMA 세션에 대한 포인터입니다.

### <a name="return-value"></a>반환 값

- **UX_SUCCESS**: (0x00) 세션이 열렸습니다.
- **UX_HOST_CLASS_PIMA_RC_SESSION_ALREADY_OPENED**: (0x201E) 세션이 이미 열려 있습니다.

### <a name="example"></a>예제

```C
/* Open a pima session. */

status = ux_host_class_pima_session_open(pima, pima_session);

if (status != UX_SUCCESS)
    return(UX_PICTBRIDGE_ERROR_SESSION_NOT_OPEN);
```

## <a name="ux_host_class_pima_session_close"></a>ux_host_class_pima_session_close

개시 장치와 응답기 사이의 세션을 닫습니다.

### <a name="prototype"></a>프로토타입

```C
UINT ux_host_class_pima_session_close(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session)
```

### <a name="description"></a>Description

이 함수는 PIMA 개시 장치와 PIMA 응답기 사이에서 이전에 열린 세션을 닫습니다. 세션이 닫힌 후에는 대부분의 PIMA 명령을 더 이상 실행할 수 없습니다.

### <a name="parameters"></a>매개 변수

- **pima**: PIMA 클래스 인스턴스에 대한 포인터입니다.
- **pima_session**: PIMA 세션에 대한 포인터입니다.

### <a name="return-value"></a>반환 값

- **UX_SUCCESS**: (0x00) 세션이 닫혔습니다.
- **UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) 세션이 열리지 않았습니다.

### <a name="example"></a>예제

```C
/* Close the pima session. */

status = ux_host_class_pima_session_close(pima, pima_session);
```

## <a name="ux_host_class_pima_storage_ids_get"></a>ux_host_class_pima_storage_ids_get

응답기에서 스토리지 ID 배열을 가져옵니다.

### <a name="prototype"></a>프로토타입

```C
UINT ux_host_class_pima_storage_ids_get(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    ULONG *storage_ids_array,
    ULONG storage_id_length)
```

### <a name="description"></a>Description

이 함수는 응답기에서 스토리지 ID 배열을 가져옵니다.

### <a name="parameters"></a>매개 변수

- **pima**: PIMA 클래스 인스턴스에 대한 포인터입니다.
- **pima_session**: PIMA 세션에 대한 포인터입니다.
- **storage_ids_array**: 스토리지 ID를 반환하는 배열입니다.
- **storage_id_length**: 스토리지 배열의 길이입니다.

### <a name="return-value"></a>반환 값

- **UX_SUCCESS**: (0x00) 스토리지 ID 배열이 채워져 있습니다.
- **UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) 세션이 열리지 않았습니다.
- **UX_MEMORY_INSUFFICIENT**: (0x12) 메모리가 부족하여 PIMA 명령을 만들 수 없습니다.

### <a name="example"></a>예제

```C
/* Get the number of storage IDs. */
status = ux_host_class_pima_storage_ids_get(pima, pima_session,
    pictbridge ->ux_pictbridge_storage_ids, 64);

if (status != UX_SUCCESS)
{
    /* Close the pima session. */
    status = ux_host_class_pima_session_close(pima, pima_session);

    return(UX_PICTBRIDGE_ERROR_STORE_NOT_AVAILABLE);
}
```

## <a name="ux_host_class_pima_storage_info_get"></a>ux_host_class_pima_storage_info_get

응답기로부터 스토리지 정보를 가져옵니다.

### <a name="prototype"></a>프로토타입

```C
UINT ux_host_class_pima_storage_info_get(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    ULONG storage_id,
    UX_HOST_CLASS_PIMA_STORAGE *storage)
```

### <a name="description"></a>Description

이 함수는 *storage_id* 값의 스토리지 컨테이너에 대한 스토리지 정보를 가져옵니다.

### <a name="parameters"></a>매개 변수

- **pima**: PIMA 클래스 인스턴스에 대한 포인터입니다.
- **pima_session**: PIMA 세션에 대한 포인터입니다.
- **storage_id**: 스토리지 컨테이너의 ID입니다.
- **storage**: 스토리지 정보 컨테이너에 대한 포인터입니다.

### <a name="return-value"></a>반환 값

- **UX_SUCCESS**: (0x00) 스토리지 정보가 검색되었습니다.
- **UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) 세션이 열리지 않았습니다.
- **UX_MEMORY_INSUFFICIENT**: (0x12) 메모리가 부족하여 PIMA 명령을 만들 수 없습니다.

### <a name="example"></a>예제

```C
/* Get the first storage ID info container. */
status = ux_host_class_pima_storage_info_get(pima, pima_session,
    pictbridge ->ux_pictbridge_storage_ids[0],
    (UX_HOST_CLASS_PIMA_STORAGE *)pictbridge ->ux_pictbridge_storage);

if (status != UX_SUCCESS)
{
    /* Close the pima session. */
    status = ux_host_class_pima_session_close(pictbridge ->
        ux_pictbridge_pima, pima_session);
    return(UX_PICTBRIDGE_ERROR_STORE_NOT_AVAILABLE);
}
```

## <a name="ux_host_class_pima_num_objects_get"></a>ux_host_class_pima_num_objects_get

응답기에서 스토리지 컨테이너의 개체 수를 가져옵니다.

### <a name="prototype"></a>프로토타입

```C
UINT ux_host_class_pima_num_objects_get(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    ULONG storage_id,
    ULONG object_format_code)
```

### <a name="description"></a>Description

이 함수는 특정 형식 코드와 일치하는 storage_id 값의 특정 스토리지 컨테이너에 저장된 개체 수를 가져옵니다. 개체 수는 pima_session 구조의 ux_host_class_pima_session_nb_objects 필드에서 반환됩니다.

### <a name="parameters"></a>매개 변수

- **pima**: PIMA 클래스 인스턴스에 대한 포인터입니다.
- **pima_session**: PIMA 세션에 대한 포인터입니다.
- **storage_id**: 스토리지 컨테이너의 ID입니다.
- **object_format_code**: 개체 형식 코드 필터입니다.

개체 형식 코드는 다음 값 중 하나가 있어야 합니다.

| 개체 형식 코드               | Description   |     USBX 코드                          |
|----------------------------------|---------------|------------------------------------------|
| 0x3000                           | 정의되지 않음 정의되지 않은 이미지 개체 | UX_HOST_CLASS_PIMA_OFC_UNDEFINED   |
| 0x3001                           | 연결 연결(예: 폴더) | UX_HOST_CLASS_PIMA_OFC_ASSOCIATION |
| 0x3002                           | 스크립트 디바이스 모델별 스크립트 | UX_HOST_CLASS_PIMA_OFC_SCRIPT      |
| 0x3003                           | 실행 파일 디바이스 모델별 이진 실행 파일 | UX_HOST_CLASS_PIMA_OFC_EXECUTABLE  |
| 0x3004                           | 텍스트 텍스트 파일  |   UX_HOST_CLASS_PIMA_OFC_TEXT        |
| 0x3005                           | HTML HyperText Markup Language 파일(텍스트) | UX_HOST_CLASS_PIMA_OFC_HTML        |
| 0x3006                           | DPOF Digital Print Order Format 파일(텍스트) | UX_HOST_CLASS_PIMA_OFC_DPOF        |
| 0x3007                           | AIFF 오디오 클립  |  UX_HOST_CLASS_PIMA_OFC_AIFF        |
| 0x3008                           | WAV 오디오 클립   |  UX_HOST_CLASS_PIMA_OFC_WAV         |
| 0x3009                           | MP3 오디오 클립   |  UX_HOST_CLASS_PIMA_OFC_MP3         |
| 0x300A                           | AVI 동영상 클립   |  UX_HOST_CLASS_PIMA_OFC_AVI         |
| 0x300B                           | MPEG 동영상 클립  |  UX_HOST_CLASS_PIMA_OFC_MPEG        |
| 0x300C                           | ASF Microsoft Advanced Streaming Format(동영상) | UX_HOST_CLASS_PIMA_OFC_ASF         |
| 0x3800                           | 정의되지 않음 알 수 없는 이미지 개체 | UX_HOST_CLASS_PIMA_OFC_QT          |
| 0x3801                           | EXIF/JPEG 교환 파일 형식, JEIDA 표준 | UX_HOST_CLASS_PIMA_OFC_EXIF_JPEG   |
| 0x3802                           | TIFF/EP TIFF/EP(Tag Image File Format for Electronic Photography) | UX_HOST_CLASS_PIMA_OFC_TIFF_EP     |
| 0x3803                           | FlashPix 구조적 스토리지 이미지 형식 | UX_HOST_CLASS_PIMA_OFC_FLASHPIX    |
| 0x3804                           | BMP Microsoft Windows 비트맵 파일 | UX_HOST_CLASS_PIMA_OFC_BMP         |
| 0x3805                           | CIFF Canon 카메라 이미지 파일 형식 | UX_HOST_CLASS_PIMA_OFC_CIFF        |
| 0x3806                           | 정의되지 않음 예약됨 |  |
| 0x3807                           | GIF Graphics Interchange Format | UX_HOST_CLASS_PIMA_OFC_GIF         |
| 0x3808                           | JFIF JPEG 파일 교환 형식 | UX_HOST_CLASS_PIMA_OFC_JFIF        |
| 0x3809                           | PCD PhotoCD 이미지 팩 | UX_HOST_CLASS_PIMA_OFC_PCD         |
| 0x380A                           | PICT Quickdraw 이미지 형식 | UX_HOST_CLASS_PIMA_OFC_PICT        |
| 0x380B                           | PNG 이동식 네트워크 그래픽 | UX_HOST_CLASS_PIMA_OFC_PNG         |
| 0x380C                           | 정의되지 않음 예약됨 |   |
| 0x380D                           | TIFF Tag Image File Format | UX_HOST_CLASS_PIMA_OFC_TIFF        |
| 0x380E                           | TIFF/IT TIFF/IT(Tag Image File Format for Information Technology)(그래픽 아트) | UX_HOST_CLASS_PIMA_OFC_TIFF_IT     |
| 0x380F                           | JP2 JPEG2000 기준 파일 형식 | UX_HOST_CLASS_PIMA_OFC_JP2         |
| 0x3810                           | JPX JPEG2000 확장 파일 형식 | UX_HOST_CLASS_PIMA_OFC_JPX         |
| MSN 0011을 사용하는 기타 모든 코드 | 이후 사용을 위해 정의되지 않은 모든 예약 |                                    |
| MSN 1011을 사용하는 기타 모든 코드 | 공급업체에서 정의한 공급업체 정의 형식: 이미지 |                                    |

### <a name="return-value"></a>반환 값

- **UX_SUCCESS**: (0x00) 데이터 전송이 완료되었습니다.
- **UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) 세션이 열리지 않았습니다.
- **UX_MEMORY_INSUFFICIENT**: (0x12) 메모리가 부족하여 PIMA 명령을 만들 수 없습니다.

### <a name="example"></a>예제

```C
/* Get the number of objects on all containers matching a SCRIPT object. */
status = ux_host_class_pima_num_objects_get(pima, pima_session,
    UX_PICTBRIDGE_ALL_CONTAINERS, UX_PICTBRIDGE_OBJECT_SCRIPT);

if (status != UX_SUCCESS)
{
    /* Close the pima session. */
    status = ux_**host_class_pima_session_close(pima, pima_session);

    return(UX_PICTBRIDGE_ERROR_STORE_NOT_AVAILABLE);
} else
    /* The number of objects is returned in the field: pima_session -> ux_host_class_pima_session_nb_objects */
```

## <a name="ux_host_class_pima_object_handles_get"></a>ux_host_class_pima_object_handles_get

응답기에서 개체 핸들을 가져옵니다.

### <a name="prototype"></a>프로토타입

```C
UINT ux_host_class_pima_object_handles_get(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    ULONG *object_handles_array,
    ULONG object_handles_length,
    ULONG storage_id,
    ULONG object_format_code,
    ULONG object_handle_association)
```

### <a name="description"></a>Description

Storage_id 매개 변수로 표시되는 스토리지 컨테이너에 있는 개체 핸들의 배열을 반환합니다. 모든 저장소에서 집계된 목록이 필요한 경우 이 값은 0xFFFFFFFF로 설정되어야 합니다.

### <a name="parameters"></a>매개 변수

- **pima**: PIMA 클래스 인스턴스에 대한 포인터입니다.
- **pima_session**: PIMA 세션에 대한 포인터입니다.
- **object_handes_array**: 핸들이 반환되는 배열입니다.
- **object_handles_length**: 배열의 길이입니다.
- **storage_id**: 스토리지 컨테이너의 ID입니다.
- **object_format_code**: 개체의 서식 코드입니다(함수 ux_host_class_pima_num_objects_get에 대한 테이블 참조).
- **object_handle_association**: 선택적 개체 연결 값입니다.

개체 핸들 연결은 아래 표의 나오는 값 중 하나일 수 있습니다.

| AssociationCode                        | AssociationType      | 해석       |
|----------------------------------------|----------------------|----------------------|
| 0x0000                                 | Undefined            | Undefined            |
| 0x0001                                 | GenericFolder        | 사용 안 함               |
| 0x0002                                 | Album                | 예약됨             |
| 0x0003                                 | TimeSequence         | DefaultPlaybackDelta |
| 0x0004                                 | HorizontalPanoramic  | 사용 안 함               |
| 0x0005                                 | VerticalPanoramic    | 사용 안 함               |
| 0x0006                                 | 2DPanoramic          | ImagesPerRow         |
| 0x0007                                 | AncillaryData        | 정의되지 않음            |
| 비트가 15인 다른 모든 값이 0으로 설정됩니다.  | 예약됨             | 정의되지 않음            |
| 비트가 15인 모든 값이 1로 설정됩니다.        | 공급업체 정의       | 공급업체 정의       |

### <a name="return-value"></a>반환 값

- **UX_SUCCESS**: (0x00) 데이터 전송이 완료되었습니다.
- **UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) 세션이 열리지 않았습니다.
- **UX_MEMORY_INSUFFICIENT**: (0x12) 메모리가 부족하여 PIMA 명령을 만들 수 없습니다.

### <a name="example"></a>예제

```C
/* Get the array of objects handles on the container. */
status = ux_**host_class_pima_object_handles_get(pima, pima_session,
    pictbridge ->ux_pictbridge_object_handles_array,
    4 * pima_session ->ux_host_class_pima_session_nb_objects,
    UX_PICTBRIDGE_ALL_CONTAINERS,
    UX_PICTBRIDGE_OBJECT_SCRIPT, 0);

if (status != UX_SUCCESS)
{
    /* Close the pima session. */
    status = ux_host_class_pima_session_close(pima, pima_session);
    return(UX_PICTBRIDGE_ERROR_STORE_NOT_AVAILABLE);
}
```

## <a name="ux_host_class_pima_object_info_get"></a>ux_host_class_pima_object_info_get

응답기에서 개체 정보를 가져옵니다.

### <a name="prototype"></a>프로토타입

```C
UINT ux_host_class_pima_object_info_get(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    ULONG object_handle,
    UX_HOST_CLASS_PIMA_OBJECT *object)
```

### <a name="description"></a>Description

이 함수는 개체 핸들에 대한 개체 정보를 가져옵니다.

### <a name="parameters"></a>매개 변수

- **pima**: PIMA 클래스 인스턴스에 대한 포인터입니다.
- **pima_session**: PIMA 세션에 대한 포인터입니다.
- **object_handle**: 개체의 핸들입니다.
- **object**: 개체 정보 컨테이너에 대한 포인터입니다.

### <a name="return-value"></a>반환 값

- **UX_SUCCESS**: (0x00) 데이터 전송이 완료되었습니다.
- **UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) 세션이 열리지 않았습니다.
- **UX_MEMORY_INSUFFICIENT**: (0x12) 메모리가 부족하여 PIMA 명령을 만들 수 없습니다.

### <a name="example"></a>예제

```C
/* We search for an object that is a picture or a script. */
object_index = 0;

while (object_index < pima_session -> ux_host_class_pima_session_nb_objects)
{
    /* Get the object info structure. */
    status = ux_**host_class_pima_object_info_get(pima, pima_session,
        pictbridge -> ux_pictbridge_object_handles_array[object_index], 
        pima_object);

    if (status != UX_SUCCESS)
    {
        /* Close the pima session. */
        status = ux_host_class_pima_session_close(pima, pima_session);

        return(UX_PICTBRIDGE_ERROR_INVALID_OBJECT_HANDLE );
    }
}
```

## <a name="ux_host_class_pima_object_info_send"></a>ux_host_class_pima_object_info_send

개체 정보를 응답기로 보냅니다.

### <a name="prototype"></a>프로토타입

```C
UINT ux_host_class_pima_object_info_send(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    ULONG storage_id,
    ULONG parent_object_id,
    UX_HOST_CLASS_PIMA_OBJECT *object)
```

### <a name="description"></a>Description

이 함수는 storage_id 값의 스토리지 컨테이너에 대한 스토리지 정보를 보냅니다. 개시 장치는 개체를 응답기로 보내기 전에 이 명령을 사용해야 합니다.

### <a name="parameters"></a>매개 변수

- **pima**: PIMA 클래스 인스턴스에 대한 포인터입니다.
- **pima_session**: PIMA 세션에 대한 포인터입니다.
- **storage_id**: 대상 스토리지 ID입니다.
- **parent_object_id**: 개체를 배치해야 하는 응답기의 부모 ObjectHandle입니다.
- **object**: 개체 정보 컨테이너에 대한 포인터입니다.

### <a name="return-value"></a>반환 값

- **UX_SUCCESS**: (0x00) 데이터 전송이 완료되었습니다.
- **UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) 세션이 열리지 않았습니다.
- **UX_MEMORY_INSUFFICIENT**: (0x12) 메모리가 부족하여 PIMA 명령을 만들 수 없습니다.

### <a name="example"></a>예제

```C
/* Send a script info. */
status = ux_host_class_pima_object_info_send(pima, pima_session,
    0, 0, pima_object);

if (status != UX_SUCCESS)
{
    /* Close the pima session. */
    status = ux_host_class_pima_session_close(pima, pima_session);

    return(UX_ERROR);
}
```

## <a name="ux_host_class_pima_object_open"></a>ux_host_class_pima_object_open

응답기에 저장된 개체를 엽니다.

### <a name="prototype"></a>프로토타입

```C
UINT ux_host_class_pima_object_open(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    ULONG object_handle,
    UX_HOST_CLASS_PIMA_OBJECT *object)
```

### <a name="description"></a>Description

이 함수는 읽거나 쓰기 전에 응답기에서 개체를 엽니다.

### <a name="parameters"></a>매개 변수

- **pima**: PIMA 클래스 인스턴스에 대한 포인터입니다.
- **pima_session**: PIMA 세션에 대한 포인터입니다.
- **object_handle**: 개체의 핸들입니다.
- **object**: 개체 정보 컨테이너에 대한 포인터입니다.

### <a name="return-value"></a>반환 값

- **UX_SUCCESS**: (0x00) 데이터 전송이 완료되었습니다.
- **UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) 세션이 열리지 않았습니다.
- **UX_HOST_CLASS_PIMA_RC_OBJECT_ALREADY_OPENED**: (0x2021) 개체가 이미 열려 있습니다.
- **UX_MEMORY_INSUFFICIENT**: (0x12) 메모리가 부족하여 PIMA 명령을 만들 수 없습니다.

### <a name="example"></a>예제

```C
/* Open the object. */

status = ux_host_class_pima_object_open(pima, pima_session,
    object_handle, pima_object);

/* Check status. */
if (status != UX_SUCCESS)
    return(status);
```

## <a name="ux_host_class_pima_object_get"></a>ux_host_class_pima_object_get

응답기에 저장된 개체를 가져옵니다.

### <a name="prototype"></a>프로토타입

```C
UINT ux_host_class_pima_object_get(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    ULONG object_handle,
    UX_HOST_CLASS_PIMA_OBJECT *object,
    UCHAR *object_buffer,
    ULONG object_buffer_length,
    ULONG *object_actual_length)
```

### <a name="description"></a>Description

이 함수는 응답기에서 개체를 가져옵니다.

### <a name="parameters"></a>매개 변수

- **pima**: PIMA 클래스 인스턴스에 대한 포인터입니다.
- **pima_session**: PIMA 세션에 대한 포인터입니다.
- **object_handle**: 개체의 핸들입니다.
- **object**: 개체 정보 컨테이너에 대한 포인터입니다.
- **object_buffer**: 개체 데이터의 주소입니다.
- **object_buffer_length**: 요청된 개체의 길이입니다.
- **object_actual_length**: 반환되는 개체의 길이입니다.

### <a name="return-value"></a>반환 값

- **UX_SUCCESS**: (0x00) 개체가 전송되었습니다.
- **UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) 세션이 열리지 않았습니다.
- **UX_HOST_CLASS_PIMA_RC_OBJECT_NOT_OPENED**: (0x2023) 개체가 열리지 않았습니다.
- **UX_HOST_CLASS_PIMA_RC_ACCESS_DENIED**: (0x200f) 개체에 대한 액세스가 거부되었습니다.
- **UX_HOST_CLASS_PIMA_RC_INCOMPLETE_TRANSFER**: (0x2007) 전송이 완료되지 않았습니다.
- **UX_MEMORY_INSUFFICIENT**: (0x12) 메모리가 부족하여 PIMA 명령을 만들 수 없습니다.
- **UX_TRANSFER_ERROR**: (0x23) 개체를 읽는 동안 전송 오류가 발생했습니다.

### <a name="example"></a>예제

```C
/* Open the object. */

status = ux_host_class_pima_object_open(pima, pima_session,
    object_handle, pima_object);

/* Check status. */
if (status != UX_SUCCESS)
    return(status);

/* Set the object buffer pointer. */
object_buffer = pima_object ->ux_host_class_pima_object_buffer;

/* Obtain all the object data. */
while(object_length != 0)
{
    /* Calculate what length to request. */
    if (object_length > UX_PICTBRIDGE_MAX_PIMA_OBJECT_BUFFER)
        /* Request maximum length. */
        requested_length = UX_PICTBRIDGE_MAX_PIMA_OBJECT_BUFFER;
    else
        /* Request remaining length. */
        requested_length = object_length;

    /* Get the object data. */
    status = ux_host_class_pima_object_get(pima, pima_session,
        object_handle, pima_object, object_buffer,
        requested_length, &actual_length);

    if (status != UX_SUCCESS)
    {
        /* We had a problem, abort the transfer. */
        ux_host_class_pima_object_transfer_abort(pima, pima_session,
            object_handle, pima_object);

        /* And close the object. */
        ux_host_class_pima_object_close(pima, pima_session,
            object_handle, pima_object, object);

        return(status);

    }

    /* We have received some data, update the length remaining. */
    object_length -= actual_length;

    /* Update the buffer address. */
    object_buffer += actual_length;

}

/* Close the object. */
status = ux_host_class_pima_object_close(pima, pima_session,
    object_handle, pima_object, object);
```

## <a name="ux_host_class_pima_object_send"></a>ux_host_class_pima_object_send

응답기에 저장된 개체를 보냅니다.

### <a name="prototype"></a>프로토타입

```C
UINT ux_host_class_pima_object_send(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    UX_HOST_CLASS_PIMA_OBJECT *object,
    UCHAR *object_buffer, ULONG object_buffer_length)
```

### <a name="description"></a>Description

이 함수는 개체를 응답기로 보냅니다.

### <a name="parameters"></a>매개 변수

- **pima**: PIMA 클래스 인스턴스에 대한 포인터입니다.
- **pima_sessio**: PIMA 세션에 대한 포인터입니다.
- **object_handle**: 개체의 핸들입니다.
- **object**: 개체 정보 컨테이너에 대한 포인터입니다.
- **object_buffer**: 개체 데이터의 주소입니다.
- **object_buffer_length**: 요청된 개체의 길이입니다.

### <a name="return-value"></a>반환 값

- **UX_SUCCESS**: (0x00) 데이터 전송이 완료되었습니다.
- **UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) 세션이 열리지 않았습니다.
- **UX_HOST_CLASS_PIMA_RC_OBJECT_NOT_OPENED**: (0x2023) 개체가 열리지 않았습니다.
- **UX_HOST_CLASS_PIMA_RC_ACCESS_DENIED**: (0x200f) 개체에 대한 액세스가 거부되었습니다.
- **UX_HOST_CLASS_PIMA_RC_INCOMPLETE_TRANSFER**: (0x2007) 전송이 완료되지 않았습니다.
- **UX_MEMORY_INSUFFICIENT**: (0x12) 메모리가 부족하여 PIMA 명령을 만들 수 없습니다.
- **UX_TRANSFER_ERROR**: (0x23) 개체를 쓰는 동안 전송 오류가 발생했습니다.

### <a name="example"></a>예제

```C
/* Open the object. */
status = ux_host_class_pima_object_open(pima, pima_session,
    object_handle, pima_object);

/* Get the object length. */
object_length = pima_object ->ux_host_class_pima_object_compressed_size;

/* Recall the object buffer address. */
pima_object_buffer = pima_object ->ux_host_class_pima_object_buffer;

/* Send all the object data. */
while(object_length != 0)
{
    /* Calculate what length to request. */
    if (object_length > UX_PICTBRIDGE_MAX_PIMA_OBJECT_BUFFER)
        /* Request maximum length. */
        requested_length = UX_PICTBRIDGE_MAX_PIMA_OBJECT_BUFFER;
    else
        /* Request remaining length. */
        requested_length = object_length;

    /* Send the object data. */
    status = ux_host_class_pima_object_send(pima,
        pima_session, pima_object,
        pima_object_buffer, requested_length);

    if (status != UX_SUCCESS)
    {
        /* Abort the transfer. */
        ux_host_class_pima_object_transfer_abort(pima, pima_session,
            object_handle, pima_object);

        /* Return status. */
        return(status);
    }

    /* We have sent some data, update the length remaining. */
    object_length -= requested_length;
}

/* Close the object. */
status = ux_host_class_pima_object_close(pima, pima_session, object_handle,
    pima_object, object);
```

## <a name="ux_host_class_pima_thumb_get"></a>ux_host_class_pima_thumb_get

응답기에 저장된 thumb 개체를 가져옵니다.

### <a name="prototype"></a>프로토타입

```C
UINT ux_host_class_pima_thumb_get(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    ULONG object_handle,
    UX_HOST_CLASS_PIMA_OBJECT *object,
    UCHAR *thumb_buffer, ULONG thumb_buffer_length,
    ULONG *thumb_actual_length)
```

### <a name="description"></a>Description

이 함수는 응답기의 thumb 개체를 가져옵니다.

### <a name="parameters"></a>매개 변수

- **pima**: PIMA 클래스 인스턴스에 대한 포인터입니다.
- **pima_session**: PIMA 세션에 대한 포인터입니다.
- **object_handle**: 개체의 핸들입니다.
- **object**: 개체 정보 컨테이너에 대한 포인터입니다.
- **thumb_buffer**: thumb 개체 데이터의 주소입니다.
- **thumb_buffer_length**: 요청된 thumb 개체의 길이입니다.
- **thumb_actual_length**: 반환되는 thumb 개체의 길이입니다.

### <a name="return-value"></a>반환 값

- **UX_SUCCESS**: (0x00) 데이터 전송이 완료되었습니다.
- **UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) 세션이 열리지 않았습니다.
- **UX_HOST_CLASS_PIMA_RC_OBJECT_NOT_OPENED**: (0x2023) 개체가 열리지 않았습니다.
- **UX_HOST_CLASS_PIMA_RC_ACCESS_DENIED**: (0x200f) 개체에 대한 액세스가 거부되었습니다.
- **UX_HOST_CLASS_PIMA_RC_INCOMPLETE_TRANSFER**: (0x2007) 전송이 완료되지 않았습니다.
- **UX_MEMORY_INSUFFICIENT**: (0x12) 메모리가 부족하여 PIMA 명령을 만들 수 없습니다.
- **UX_TRANSFER_ERROR**: (0x23) 개체를 읽는 동안 전송 오류가 발생했습니다.

### <a name="example"></a>예제

```C
/* Get the thumb object data. */

status = ux_host_class_pima_thumb_get(pima, pima_session,
    object_handle, pima_object, object_buffer,
    requested_length, &actual_length);

if (status != UX_SUCCESS)
{
    /* And close the object. */
    ux_host_class_pima_object_close(pima, pima_session, object_handle, pima_object, object);

    return(status);
}
```

## <a name="ux_host_class_pima_object_delete"></a>ux_host_class_pima_object_delete

응답기에 저장된 개체를 삭제합니다.

### <a name="prototype"></a>프로토타입

```C
UINT ux_host_class_pima_object_delete(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    ULONG object_handle)
```

### <a name="description"></a>Description

이 함수는 응답기에서 개체를 삭제합니다.

### <a name="parameters"></a>매개 변수

- **pima**: PIMA 클래스 인스턴스에 대한 포인터입니다.
- **pima_session**: PIMA 세션에 대한 포인터입니다.
- **object_handle**: 개체의 핸들입니다.

### <a name="return-value"></a>반환 값

- **UX_SUCCESS**: (0x00) 개체가 삭제되었습니다.
- **UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) 세션이 열리지 않았습니다.
- **UX_HOST_CLASS_PIMA_RC_ACCESS_DENIED**: (0x200f) 개체를 삭제할 수 없습니다.
- **UX_MEMORY_INSUFFICIENT**: (0x12) 메모리가 부족하여 PIMA 명령을 만들 수 없습니다.

### <a name="example"></a>예제

```C
/* Delete the object. */
status = ux_host_class_pima_object_delete(pima, pima_session, object_handle, pima_object);

/* Check status. */
if (status != UX_SUCCESS)
    return(status);
```

## <a name="ux_host_class_pima_object_close"></a>ux_host_class_pima_object_close

응답기에 저장된 개체를 닫습니다.

### <a name="prototype"></a>프로토타입

```C
UINT ux_host_class_pima_object_close(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    ULONG object_handle, UX_HOST_CLASS_PIMA_OBJECT *object)
```

### <a name="description"></a>Description

이 함수는 응답기에서 개체를 닫습니다.

### <a name="parameters"></a>매개 변수

- **pima**: PIMA 클래스 인스턴스에 대한 포인터입니다.
- **pima_session**: PIMA 세션에 대한 포인터입니다.
- **object_handle**: 개체의 핸들입니다.
- **object** 개체에 대한 포인터입니다.

### <a name="return-value"></a>반환 값

- **UX_SUCCESS**: (0x00) 개체가 닫혔습니다.
- **UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) 세션이 열리지 않았습니다.
- **UX_HOST_CLASS_PIMA_RC_OBJECT_NOT_OPENED**: (0x2023) 개체가 열리지 않았습니다.
- **UX_MEMORY_INSUFFICIENT**: (0x12) 메모리가 부족하여 PIMA 명령을 만들 수 없습니다.

### <a name="example"></a>예제

```C
/* Close the object. */
status = ux_host_class_pima_object_close(pima, pima_session, object_handle, object);
```

## <a name="ux_host_class_gser_read"></a>ux_host_class_gser_read

일반 직렬 인터페이스에서 읽습니다.

### <a name="prototype"></a>프로토타입

```C
UINT ux_host_class_gser_read(
    UX_HOST_CLASS_GSER *gser,
    ULONG interface_index,
    UCHAR *data_pointer,
    ULONG requested_length,
    ULONG *actual_length)
```

### <a name="description"></a>Description

이 함수는 일반 직렬 인터페이스에서 읽습니다. 호출이 차단되고 오류가 있거나 전송이 완료된 경우에만 반환합니다.

### <a name="parameters"></a>매개 변수

- **gser**: gser 클래스 인스턴스에 대한 포인터입니다.
- **interface_index** 읽을 인터페이스 인덱스입니다.
- **data_pointer**: 데이터 페이로드의 버퍼 주소에 대한 포인터입니다.
- **requested_length**: 수신될 길이입니다.
- **actual_length**: 실제로 수신된 길이입니다.

### <a name="return-value"></a>반환 값

- **UX_SUCCESS**: (0x00) 데이터 전송이 완료되었습니다.
- **UX_TRANSFER_TIMEOUT**: (0x5c) 전송 시간 제한을 초과했습니다. 읽기가 완료되지 않았습니다.

### <a name="example"></a>예제

```C
UINT status;

/* The following example illustrates this service. */
status = ux_host_class_gser_read(cdc_acm, interface_index,data_pointer, requested_length, &actual_length);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_gser_write"></a>ux_host_class_gser_write

일반 직렬 인터페이스에 씁니다.

### <a name="prototype"></a>프로토타입

```C
UINT ux_host_class_gser_write(
    UX_HOST_CLASS_GSER *gser,
    ULONG interface_index,
    UCHAR *data_pointer,
    ULONG requested_length,
    ULONG *actual_length)
```

### <a name="description"></a>Description

이 함수는 일반 직렬 인터페이스에 씁니다. 호출이 차단되고 오류가 있거나 전송이 완료된 경우에만 반환합니다.

### <a name="parameters"></a>매개 변수

- **gser**: gser 클래스 인스턴스에 대한 포인터입니다.
- **interface_index**: 쓰기 작업의 대상 인터페이스입니다.
- **data_pointer**: 데이터 페이로드의 버퍼 주소에 대한 포인터입니다.
- **requested_length**: 전송될 길이입니다.
- **actual_length**: 실제로 전송된 길이입니다.

### <a name="return-value"></a>반환 값

- **UX_SUCCESS**: (0x00) 데이터 전송이 완료되었습니다.
- **UX_TRANSFER_TIMEOUT**: (0x5c) 전송 시간 제한을 초과했습니다. 쓰기가 완료되지 않았습니다.

### <a name="example"></a>예제

```C
UINT status;

/* The following example illustrates this service. */
status = ux_host_class_cdc_acm_write(gser, data_pointer, requested_length, &actual_length);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_gser_ioctl"></a>ux_host_class_gser_ioctl

일반 직렬 인터페이스에 대한 IOCTL 함수를 실행합니다.

### <a name="prototype"></a>프로토타입

```C
UINT ux_host_class_gser_ioctl(
    UX_HOST_CLASS_GSER *gser,
    ULONG ioctl_function,
    VOID *parameter)
```

### <a name="description"></a>Description

이 함수는 gser 인터페이스에 대한 특정 ioctl 함수를 실행합니다. 호출이 차단되고 오류가 있거나 명령이 완료된 경우에만 반환합니다.

### <a name="parameters"></a>매개 변수

- **gser**: gser 클래스 인스턴스에 대한 포인터입니다.
- **ioctl_function**: 실행할 ioctl 함수입니다. 허용되는 ioctl 함수 중 하나에 대해서는 아래 테이블 중 하나를 참조하세요.
- **parameter**: ioctl 호출과 관련된 매개 변수에 대한 포인터입니다.

### <a name="return-value"></a>반환 값

- **UX_SUCCESS**: (0x00) 데이터 전송이 완료되었습니다.
- **UX_MEMORY_INSUFFICIENT**: (0x12) 메모리가 부족합니다.
- **UX_HOST_CLASS_UNKNOWN**: (0x59) 잘못된 클래스 인스턴스입니다.
- **UX_FUNCTION_NOT_SUPPORTED**: (0x54) 알 수 없는 IOCTL 함수입니다.

### <a name="ioctl-functions"></a>IOCTL 함수

- UX_HOST_CLASS_GSER_IOCTL_SET_LINE_CODING
- UX_HOST_CLASS_GSER_IOCTL_GET_LINE_CODING
- UX_HOST_CLASS_GSER_IOCTL_SET_LINE_STATE
- UX_HOST_CLASS_GSER_IOCTL_SEND_BREAK
- UX_HOST_CLASS_GSER_IOCTL_ABORT_IN_PIPE
- UX_HOST_CLASS_GSER_IOCTL_ABORT_OUT_PIPE
- UX_HOST_CLASS_GSER_IOCTL_NOTIFICATION_CALLBACK
- UX_HOST_CLASS_GSER_IOCTL_GET_DEVICE_STATUS

### <a name="example"></a>예제

```C
UINT status;

/* The following example illustrates this service. */

status = ux_host_class_gser_ioctl(gser,
    UX_HOST_CLASS_GSER_IOCTL_GET_LINE_CODING,
    (VOID *)&line_coding);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_gser_reception_start"></a>ux_host_class_gser_reception_start

일반 직렬 인터페이스에서 수신을 시작합니다.

### <a name="prototype"></a>프로토타입

```C
UINT ux_host_class_gser_reception_start(
    UX_HOST_CLASS_GSER *gser,
    UX_HOST_CLASS_GSER_RECEPTION *gser_reception)
```

### <a name="description"></a>Description

이 함수는 일반 직렬 클래스 인터페이스에서 수신을 시작합니다. 이 함수는 비차단 수신을 허용합니다. 버퍼를 수신하면 콜백은 애플리케이션으로 호출됩니다.

### <a name="parameters"></a>매개 변수

- **gser** gser 클래스 인스턴스에 대한 포인터입니다.
- **gser_reception** 수신 매개 변수를 포함하는 구조체입니다.

### <a name="return-value"></a>반환 값

- **UX_SUCCESS** (0x00) 데이터 전송이 완료되었습니다.
- **UX_HOST_CLASS_UNKNOWN** (0x59) 잘못된 클래스 인스턴스입니다.
- **UX_ERROR** (0x01) 오류입니다.

### <a name="example"></a>예제

```C
/* Start the reception for gser. AT commands are on interface 2. */
gser_reception.ux_host_class_gser_reception_interface_index =
    UX_DEMO_GSER_AT_INTERFACE;
gser_reception.ux_host_class_gser_reception_block_size =
    UX_DEMO_RECEPTION_BLOCK_SIZE;
gser_reception.ux_host_class_gser_reception_data_buffer =
    gser_reception_buffer;
gser_reception.ux_host_class_gser_reception_data_buffer_size =
    UX_DEMO_RECEPTION_BUFFER_SIZE;
gser_reception.ux_host_class_gser_reception_callback =
    tx_demo_thread_callback;

ux_host_class_gser_reception_start(gser, &gser_reception);
```

## <a name="ux_host_class_gser_reception_stop"></a>ux_host_class_gser_reception_stop

일반 직렬 인터페이스에서 수신을 중지합니다.

### <a name="prototype"></a>프로토타입

```C
UINT ux_host_class_gser_reception_stop(
    UX_HOST_CLASS_GSER *gser,
    UX_HOST_CLASS_GSER_RECEPTION *gser_reception)
```

### <a name="description"></a>Description

이 함수는 일반 직렬 클래스 인터페이스에서 수신을 중지합니다.

### <a name="parameters"></a>매개 변수

- **gser** gser 클래스 인스턴스에 대한 포인터입니다.
- **gser_reception** 수신 매개 변수를 포함하는 구조체입니다.

### <a name="return-value"></a>반환 값

- **UX_SUCCESS** (0x00) 데이터 전송이 완료되었습니다.
- **UX_HOST_CLASS_UNKNOWN** (0x59) 잘못된 클래스 인스턴스입니다.
- **UX_ERROR** (0x01) 오류입니다.

### <a name="example"></a>예제

```C
/* Stops the reception for gser. */
ux_host_class_gser_reception_stop(gser, &gser_reception);
```
