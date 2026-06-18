# Lab 3.2 Findings

## All 3 containers running — screenshot of docker-compose ps showing Up
<img width="1920" height="712" alt="Screenshot (255)" src="https://github.com/user-attachments/assets/aacd9d84-7a47-4a18-adc3-788e9ff4bac4" />

## 4 Prometheus queries returning data — screenshots of each graph
CPU Usage
<img width="1920" height="791" alt="Screenshot (263)" src="https://github.com/user-attachments/assets/b1eea82c-259b-4462-9752-2532697c5db1" />
<img width="1920" height="825" alt="Screenshot (264)" src="https://github.com/user-attachments/assets/2d200b78-ab4a-4588-975d-e00d432e81e9" />

Memory Usage
<img width="1920" height="795" alt="Screenshot (265)" src="https://github.com/user-attachments/assets/23e2a1a7-4042-4f7f-bcbc-a9644ec15a92" />
<img width="1920" height="904" alt="Screenshot (266)" src="https://github.com/user-attachments/assets/08721c6c-edc8-480d-9e0c-14405dd932a9" />

Disk Usage
<img width="1920" height="737" alt="Screenshot (259)" src="https://github.com/user-attachments/assets/0a92e365-0814-4010-a151-1dc2690df564" />
<img width="1879" height="910" alt="Screenshot (260)" src="https://github.com/user-attachments/assets/c3d669dc-bd99-4d91-83b4-d451eaf2df54" />

Network bytes in (like bandwidth monitoring):
<img width="1920" height="721" alt="Screenshot (261)" src="https://github.com/user-attachments/assets/5b69f517-b90b-483b-af29-3b82c08e55b9" />
<img width="1895" height="904" alt="Screenshot (262)" src="https://github.com/user-attachments/assets/8ee26960-ed83-4365-a6b4-9a8ee7bcac20" />

## Grafana dashboard built with at least 3 panels — screenshot
<img width="1920" height="882" alt="Screenshot (268)" src="https://github.com/user-attachments/assets/d7083e2e-2d84-40a4-9c5c-381e21b571b5" />
<img width="1920" height="911" alt="Screenshot (270)" src="https://github.com/user-attachments/assets/17371bca-7608-4742-9be6-4e8fb5662611" />

## Written in portfolio: 'What is the difference between what Prometheus/Grafana shows and what SigNoz shows? When would you use each during a P1 incident?'
Prometheus and Grafana focus on collecting and visualizing metrics such as CPU, memory, disk, network usage, and custom application metrics.
They provide flexible dashboards and alerting, making them useful for identifying infrastructure or performance issues during a P1 incident. 
SigNoz, on the other hand, combines metrics with distributed tracing and logs, giving end-to-end visibility into requests and application behavior.
During a P1 incident, Prometheus and Grafana are typically used first to detect abnormal resource usage and service degradation, 
while SigNoz is used to trace requests, analyze logs, and pinpoint the exact component or code causing the failure.


