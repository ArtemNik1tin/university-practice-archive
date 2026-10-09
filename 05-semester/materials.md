1. Protocols for Interworking: XNFS, Version 3W [Electronic resource] : Open Group Technical Standard. — Document Number C702. — Reading : The Open Group, 1998. — ISBN 1-85912-184-5.
    - **Ссылка:** https://pubs.opengroup.org/onlinepubs/9629799/toc.htm (дата обращения: 09.10.2026)
    - **Нейросетевой обзор (Gemini):** Отраслевой стандарт The Open Group, содержащий полную спецификацию вспомогательных протоколов сетевых файловых систем, в первую очередь Network Lock Manager (NLM) версии 4 и Network Status Monitor (NSM). Описывает типы данных, структуру вызовов, правила обработки конкурентных блокировок.
    - **Зачем нужно в работе:** Основной нормативно-технический документ, специфицирующий процедуры и структуры NLM. Специфицирует асинхронные вызовы (`NLM_GRANTED`, `NLM_LOCK_MSG` и др.).

2. RFC 1813. NFS Version 3 Protocol Specification [Electronic resource] / B. Callaghan, B. Pawlowski, P. Staubach. — IETF, 1995.
    - **Ссылка:** https://datatracker.ietf.org/doc/html/rfc1813 (дата обращения: 09.10.2026).
    - **Нейросетевой обзор (Gemini):** Спецификация IETF, задающая семантику и структуру сетевой файловой системы NFSv3.
    - **Зачем нужно в работе:** Базовый протокол сетевой файловой системы NFSv3.

3. RFC 5531. RPC: Remote Procedure Call Protocol Specification Version 2 [Electronic resource] / R. Thurlow. — IETF, 2009. — (Obsoletes RFC 1831 / RFC 1057).
    - **Ссылка:** https://datatracker.ietf.org/doc/html/rfc5531 (дата обращения: 09.10.2026).
    - **Нейросетевой обзор (Gemini):**: Стандарт транспортного уровня ONC RPC v2, регулирующий формат заголовков сообщений, аутентификацию (`AUTH_SYS` / `AUTH_NONE`), сопоставление номеров программ/процедур и корреляцию транзакций `XID` (Transaction ID).
    - **Зачем нужно в работе:** Реализация асинхронных вызовов в NLM требует корректного отправления RPC-запросов от сервера к клиенту без ожидания немедленного синхронного ответа, а также управления match/dispatch таблицами XID для callback-процедуры `NLM_GRANTED`.

4. RFC 4506. XDR: External Data Representation Standard [Electronic resource] / M. Eisler. — IETF, 2006. — (Obsoletes RFC 1832 / RFC 1014).
    - **Ссылка:** https://datatracker.ietf.org/doc/html/rfc4506 (дата обращения: 09.10.2026).
    - **Нейросетевой обзор (Gemini):** Описание стандарта бинарной сериализации данных XDR, обеспечивающего архитектурную независимость (big-endian выравнивание по 4 байтам, кодирование структур, объединений `discriminated union` и опциональных данных).
    - **Зачем нужно в работе:** Все структуры данных NLM (`nlm_lock`, `nlm_holder`, `nlm_testargs` и т.д.) кодируются/декодируются через XDR. Это необходимо для правильной сериализации параметров асинхронных вызовов в сетевом коде NFS Mamont.

5. RFC 1833. Binding Protocols for ONC RPC Version 2 [Electronic resource] / R. Srinivasan. — IETF, 1995.
    - **Ссылка:** https://datatracker.ietf.org/doc/html/rfc1833 (дата обращения: 09.10.2026).
    - **Нейросетевой обзор (Gemini):** Документ описывает протоколы динамического связывания портов `RPCBIND` (версий 3 и 4) и `Portmapper` (версии 2), позволяющие клиенту находить TCP/UDP порты служб по номеру программы и версии.
    - **Зачем нужно в работе:** Сервер NLM должен регистрировать свои программы и порты в `RPCBIND`, а также уметь делать обратный резолв портов клиента для выполнения callback-вызовов `NLM_GRANTED`.
