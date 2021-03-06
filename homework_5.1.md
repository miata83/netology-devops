
# Домашнее задание к занятию "5.1. Введение в виртуализацию. Типы и функции гипервизоров. Обзор рынка вендоров и областей применения."

## Задача 1

Опишите кратко, как вы поняли: в чем основное отличие полной (аппаратной) виртуализации, паравиртуализации и виртуализации на основе ОС.

## Ответ 1

Аппаратная виртуализация - гипервизор работает на аппаратном уровне, сам является операционной системой - механизмы виртуализации встроены в саму ОС хоста.   
Паравиртуализация - гостевая ОС может использовать только ресурсы, выделенные гипервизором, который стоит между гостевой и хостовой ОС -  

Разница между полной (аппаратной) и паравиртуализацией:
Полная виртуализация отличается от паравиртуализации, тем что при полной виртуализации немодифицированная ОС работает полностью изолированно. При паравиртуализации виртуальная машина не изолирует ОС полностью, а модифицирует ее, чтобы сделать ее совместимой с определенными API. Паравиртуализация работает быстрее, так как нет затрат на ненужную эмуляцию.

Виртуализация на основе ОС - контейнеры могут использовать все ресурсы хостовой ОС, т.к. нет слоя гипервизора. Разделение ресурсов происходит на уровне хостовой ОС. Преимущество в производительности и количестве развертываемых услуг на одном и том же железе.    

## Задача 2

Выберите один из вариантов использования организации физических серверов, в зависимости от условий использования.

Организация серверов:
- физические сервера,
- паравиртуализация,
- виртуализация уровня ОС.

Условия использования:
- Высоконагруженная база данных, чувствительная к отказу.
- Различные web-приложения.
- Windows системы для использования бухгалтерским отделом.
- Системы, выполняющие высокопроизводительные расчеты на GPU.

Опишите, почему вы выбрали к каждому целевому использованию такую организацию.    

## Ответ 2

- Высоконагруженная база данных, чувствительная к отказу: физические сервера, тк требуется высокая производительность, физическое аппаратное размещение дает более высокий отклик, повышается отказоустнойчивость, тк исключен слой гипервизора и хостовой ОС.
- Различные web-приложения: виртуализация уровня ОС - не требуется много ресурсов, высокая скорость масштабирования, простота обслуживания.
- Windows системы для использования бухгалтерским отделом: паравиртуализация, возможность расширения ресурсов на уровне виртуальной машины, простота выполнения бэкапов, не требуется доступ к аппаратной части серверов.
- Системы, выполняющие высокопроизводительные расчеты на GPU: физические сервера, с постоянным аппаратным доступом для модернизации. Хотя можно и облачные решения использовать, если позволяет бюджет.

## Задача 3

Выберите подходящую систему управления виртуализацией для предложенного сценария. Детально опишите ваш выбор.

Сценарии:

1. 100 виртуальных машин на базе Linux и Windows, общие задачи, нет особых требований. Преимущественно Windows based инфраструктура, требуется реализация программных балансировщиков нагрузки, репликации данных и автоматизированного механизма создания резервных копий.
2. Требуется наиболее производительное бесплатное open source решение для виртуализации небольшой (20-30 серверов) инфраструктуры на базе Linux и Windows виртуальных машин.
3. Необходимо бесплатное, максимально совместимое и производительное решение для виртуализации Windows инфраструктуры.
4. Необходимо рабочее окружение для тестирования программного продукта на нескольких дистрибутивах Linux.

## Ответ 3 
1. 100 виртуальных машин на базе Linux и Windows, общие задачи, нет особых требований. Преимущественно Windows based инфраструктура, требуется реализация программных балансировщиков нагрузки, репликации данных и автоматизированного механизма создания резервных копий.
    VMWare - высокая надежность и отказоустойчивость, слой гипервизора включается в себя требуемые механизмы для нагрузки, данных и резервных копий.    
2. Требуется наиболее производительное бесплатное open source решение для виртуализации небольшой (20-30 серверов) инфраструктуры на базе Linux и Windows виртуальных машин.
    KVM - наиболее производительное open source решение)   
3. Необходимо бесплатное, максимально совместимое и производительное решение для виртуализации Windows инфраструктуры.
    Бесплатная версия Hyper-V или KVM
4. Необходимо рабочее окружение для тестирования программного продукта на нескольких дистрибутивах Linux.
    Если требуется только Lunix, то можно рассмотреть KVM или AWS EC2

## Задача 4

Опишите возможные проблемы и недостатки гетерогенной среды виртуализации (использования нескольких систем управления виртуализацией одновременно) и что необходимо сделать для минимизации этих рисков и проблем. Если бы у вас был выбор, то создавали бы вы гетерогенную среду или нет? Мотивируйте ваш ответ примерами.

## Ответ 4
1.
- Сложность обслуживания гетерогенной среды - наличие обученного персонала для каждой среды виртуализации.
- Сложность в управлении и перемещении больших объемов данных между средами.
2. Уменьшать использование несовместимых технологий, использовать универсальные решения, обеспечить резервирование.
3. В зависимости от задачи и планирования в развитии. Наверное бы изначально выбирал в сторону универсальной и гибкой среды, чтобы не было сложности в дальнейшем использовании гетерогенных сред.


