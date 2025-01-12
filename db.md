## 1. Bảng adminprincipal
| Tên trường | Kiểu dữ liệu và độ dài | Nullable | Unique | P/F Key | Mặc định | Mô tả |
|------------|------------------------|----------|---------|---------|-----------|--------|
| principal_id | BIGINT | | | P | | ID của principal |
| principal_type_id | INTEGER | | | F | | Loại ID của principal |

## 2. Bảng adminpermission
| Tên trường | Kiểu dữ liệu và độ dài | Nullable | Unique | P/F Key | Mặc định | Mô tả |
|------------|------------------------|----------|---------|---------|-----------|--------|
| permission_id | BIGINT | | | P | | ID của permission |
| permission_name | VARCHAR(255) | | | | | Tên của permission |
| resource_type_id | INTEGER | | | F | | ID của loại resource |
| permission_label | VARCHAR(255) | | | | | Nhãn của permission |
| principal_id | BIGINT | | | F | | ID của principal |
| sort_order | SMALLINT | | | | | Thứ tự sắp xếp |

## 3. Bảng adminresourcetype
| Tên trường | Kiểu dữ liệu và độ dài | Nullable | Unique | P/F Key | Mặc định | Mô tả |
|------------|------------------------|----------|---------|---------|-----------|--------|
| resource_type_id | INTEGER | | | P | | ID của loại resource |
| resource_type_name | VARCHAR(255) | | | | | Tên của loại resource |

## 4. Bảng adminprincipaltype
| Tên trường | Kiểu dữ liệu và độ dài | Nullable | Unique | P/F Key | Mặc định | Mô tả |
|------------|------------------------|----------|---------|---------|-----------|--------|
| principal_type_id | INTEGER | | | P | | ID của loại principal |
| principal_type_name | VARCHAR(255) | | | | | Tên của loại principal |

## 5. Bảng adminprivilege
| Tên trường | Kiểu dữ liệu và độ dài | Nullable | Unique | P/F Key | Mặc định | Mô tả |
|------------|------------------------|----------|---------|---------|-----------|--------|
| privilege_id | BIGINT | | | P | | ID của privilege |
| permission_id | BIGINT | | | F | | ID của permission |
| resource_id | BIGINT | | | F | | ID của resource |
| principal_id | BIGINT | | | F | | ID của principal |

## 6. Bảng adminresource
| Tên trường | Kiểu dữ liệu và độ dài | Nullable | Unique | P/F Key | Mặc định | Mô tả |
|------------|------------------------|----------|---------|---------|-----------|--------|
| resource_id | BIGINT | | | P | | ID của resource |
| resource_type_id | INTEGER | | | F | | ID của loại resource |

## 7. Bảng alert_definition
| Tên trường | Kiểu dữ liệu và độ dài | Nullable | Unique | P/F Key | Mặc định | Mô tả |
|------------|------------------------|----------|---------|---------|-----------|--------|
| definition_id | BIGINT | | | P | | ID của định nghĩa cảnh báo |
| cluster_id | BIGINT | | | F | | ID của cluster |
| definition_name | VARCHAR(255) | | | | | Tên của định nghĩa cảnh báo |
| service_name | VARCHAR(255) | | | | | Tên service |
| component_name | VARCHAR(255) | | | | | Tên component |
| scope | VARCHAR(255) | | | | | Phạm vi |
| label | VARCHAR(255) | | | | | Nhãn |
| help_url | VARCHAR(512) | | | | | URL trợ giúp |
| description | TEXT | | | | | Mô tả chi tiết |
| enabled | SMALLINT | | | | | Trạng thái bật/tắt |
| schedule_interval | INTEGER | | | | | Khoảng thời gian lập lịch |
| source_type | VARCHAR(255) | | | | | Loại nguồn |
| alert_source | TEXT | | | | | Nguồn cảnh báo |
| hash | VARCHAR(64) | | | | | Mã hash |
| ignore_host | SMALLINT | | | | | Bỏ qua host |
| repeat_tolerance | INTEGER | | | | | Ngưỡng lặp lại |
| repeat_tolerance_enabled | SMALLINT | | | | | Trạng thái bật/tắt ngưỡng lặp lại |

## 8. Bảng alert_current
| Tên trường | Kiểu dữ liệu và độ dài | Nullable | Unique | P/F Key | Mặc định | Mô tả |
|------------|------------------------|----------|---------|---------|-----------|--------|
| alert_id | BIGINT | | | P | | ID của cảnh báo |
| definition_id | BIGINT | | | F | | ID của định nghĩa cảnh báo |
| history_id | BIGINT | | | F | | ID của lịch sử |
| maintenance_state | VARCHAR(255) | | | | | Trạng thái bảo trì |
| original_timestamp | BIGINT | | | | | Thời gian ban đầu |
| latest_timestamp | BIGINT | | | | | Thời gian mới nhất |
| latest_text | TEXT | | | | | Nội dung mới nhất |
| occurrences | BIGINT | | | | | Số lần xuất hiện |
| firmness | VARCHAR(255) | | | | | Mức độ nghiêm trọng |

## 9. Bảng alert_history
| Tên trường | Kiểu dữ liệu và độ dài | Nullable | Unique | P/F Key | Mặc định | Mô tả |
|------------|------------------------|----------|---------|---------|-----------|--------|
| alert_id | BIGINT | | | P | | ID của cảnh báo |
| cluster_id | BIGINT | | | F | | ID của cluster |
| alert_definition_id | BIGINT | | | F | | ID của định nghĩa cảnh báo |
| service_name | VARCHAR(255) | | | | | Tên service |
| component_name | VARCHAR(255) | | | | | Tên component |
| host_name | VARCHAR(255) | | | | | Tên host |
| alert_instance | VARCHAR(255) | | | | | Instance của cảnh báo |
| alert_timestamp | BIGINT | | | | | Thời gian cảnh báo |
| alert_label | VARCHAR(1024) | | | | | Nhãn cảnh báo |
| alert_state | VARCHAR(255) | | | | | Trạng thái cảnh báo |
| alert_text | TEXT | | | | | Nội dung cảnh báo |

## 10. Bảng clusters
| Tên trường | Kiểu dữ liệu và độ dài | Nullable | Unique | P/F Key | Mặc định | Mô tả |
|------------|------------------------|----------|---------|---------|-----------|--------|
| cluster_id | BIGINT | | | P | | ID của cluster |
| resource_id | BIGINT | | | F | | ID của resource |
| upgrade_id | BIGINT | | | F | | ID của nâng cấp |
| cluster_info | VARCHAR(255) | | | | | Thông tin cluster |
| cluster_name | VARCHAR(100) | | | | | Tên cluster |
| provisioning_state | VARCHAR(255) | | | | | Trạng thái cung cấp |
| security_type | VARCHAR(32) | | | | | Loại bảo mật |
| desired_cluster_state | VARCHAR(255) | | | | | Trạng thái mong muốn |
| desired_stack_id | BIGINT | | | F | | ID của stack mong muốn |

## 11. Bảng alert_group
| Tên trường | Kiểu dữ liệu và độ dài | Nullable | Unique | P/F Key | Mặc định | Mô tả |
|------------|------------------------|----------|---------|---------|-----------|--------|
| group_id | BIGINT | | | P | | ID của nhóm cảnh báo |
| cluster_id | BIGINT | | | F | | ID của cluster |
| group_name | VARCHAR(255) | | | | | Tên nhóm |
| is_default | SMALLINT | | | | | Là nhóm mặc định hay không |
| service_name | VARCHAR(255) | | | | | Tên service |

## 12. Bảng alert_group_target
| Tên trường | Kiểu dữ liệu và độ dài | Nullable | Unique | P/F Key | Mặc định | Mô tả |
|------------|------------------------|----------|---------|---------|-----------|--------|
| group_id | BIGINT | | | P,F | | ID của nhóm |
| target_id | BIGINT | | | P,F | | ID của target |

## 13. Bảng alert_target
| Tên trường | Kiểu dữ liệu và độ dài | Nullable | Unique | P/F Key | Mặc định | Mô tả |
|------------|------------------------|----------|---------|---------|-----------|--------|
| target_id | BIGINT | | | P | | ID của target |
| target_name | VARCHAR(255) | | | | | Tên target |
| notification_type | VARCHAR(64) | | | | | Loại thông báo |
| properties | TEXT | | | | | Các thuộc tính |
| description | VARCHAR(1024) | | | | | Mô tả |
| is_global | SMALLINT | | | | | Là global hay không |
| is_enabled | SMALLINT | | | | | Đang được kích hoạt hay không |

## 14. Bảng alert_grouping
| Tên trường | Kiểu dữ liệu và độ dài | Nullable | Unique | P/F Key | Mặc định | Mô tả |
|------------|------------------------|----------|---------|---------|-----------|--------|
| definition_id | BIGINT | | | P,F | | ID của định nghĩa |
| group_id | BIGINT | | | P,F | | ID của nhóm |

## 15. Bảng alert_notice
| Tên trường | Kiểu dữ liệu và độ dài | Nullable | Unique | P/F Key | Mặc định | Mô tả |
|------------|------------------------|----------|---------|---------|-----------|--------|
| notification_id | BIGINT | | | P | | ID của thông báo |
| target_id | BIGINT | | | F | | ID của target |
| history_id | BIGINT | | | F | | ID của lịch sử |
| notify_state | VARCHAR(255) | | | | | Trạng thái thông báo |
| uuid | VARCHAR(64) | | | | | UUID |

## 16. Bảng alert_target_states
| Tên trường | Kiểu dữ liệu và độ dài | Nullable | Unique | P/F Key | Mặc định | Mô tả |
|------------|------------------------|----------|---------|---------|-----------|--------|
| target_id | BIGINT | | | P,F | | ID của target |
| alert_state | VARCHAR(255) | | | P | | Trạng thái cảnh báo |

## 17. Bảng ambari_operation_history
| Tên trường | Kiểu dữ liệu và độ dài | Nullable | Unique | P/F Key | Mặc định | Mô tả |
|------------|------------------------|----------|---------|---------|-----------|--------|
| id | BIGINT | | | P | | ID của operation |
| from_version | VARCHAR(255) | | | | | Phiên bản nguồn |
| to_version | VARCHAR(255) | | | | | Phiên bản đích |
| start_time | BIGINT | | | | | Thời gian bắt đầu |
| end_time | BIGINT | | | | | Thời gian kết thúc |
| operation_type | VARCHAR(255) | | | | | Loại operation |
| comments | TEXT | | | | | Ghi chú |

## 18. Bảng ambari_sequences
| Tên trường | Kiểu dữ liệu và độ dài | Nullable | Unique | P/F Key | Mặc định | Mô tả |
|------------|------------------------|----------|---------|---------|-----------|--------|
| sequence_name | VARCHAR(255) | | | P | | Tên sequence |
| sequence_value | BIGINT | | | | | Giá trị sequence |

## 19. Bảng artifact
| Tên trường | Kiểu dữ liệu và độ dài | Nullable | Unique | P/F Key | Mặc định | Mô tả |
|------------|------------------------|----------|---------|---------|-----------|--------|
| artifact_name | VARCHAR(255) | | | P | | Tên artifact |
| artifact_data | TEXT | | | | | Dữ liệu artifact |
| foreign_keys | VARCHAR(255) | | | | | Các khóa ngoại |

## 20. Bảng stack
| Tên trường | Kiểu dữ liệu và độ dài | Nullable | Unique | P/F Key | Mặc định | Mô tả |
|------------|------------------------|----------|---------|---------|-----------|--------|
| stack_id | BIGINT | | | P | | ID của stack |
| stack_name | VARCHAR(255) | | | | | Tên stack |
| stack_version | VARCHAR(255) | | | | | Phiên bản stack |

## 21. Bảng blueprint
| Tên trường | Kiểu dữ liệu và độ dài | Nullable | Unique | P/F Key | Mặc định | Mô tả |
|------------|------------------------|----------|---------|---------|-----------|--------|
| blueprint_name | VARCHAR(255) | | | P | | Tên blueprint |
| stack_id | BIGINT | | | F | | ID của stack |
| security_type | VARCHAR(32) | | | | | Loại bảo mật |
| security_descriptor_reference | VARCHAR(255) | | | | | Tham chiếu mô tả bảo mật |

## 22. Bảng blueprint_configuration
| Tên trường | Kiểu dữ liệu và độ dài | Nullable | Unique | P/F Key | Mặc định | Mô tả |
|------------|------------------------|----------|---------|---------|-----------|--------|
| blueprint_name | VARCHAR(255) | | | P,F | | Tên blueprint |
| type_name | VARCHAR(255) | | | P | | Tên loại |
| config_data | TEXT | | | | | Dữ liệu cấu hình |
| config_attributes | TEXT | | | | | Thuộc tính cấu hình |

## 23. Bảng blueprint_setting
| Tên trường | Kiểu dữ liệu và độ dài | Nullable | Unique | P/F Key | Mặc định | Mô tả |
|------------|------------------------|----------|---------|---------|-----------|--------|
| id | BIGINT | | | P | | ID của setting |
| blueprint_name | VARCHAR(255) | | | F | | Tên blueprint |
| setting_name | VARCHAR(255) | | | | | Tên setting |
| setting_data | TEXT | | | | | Dữ liệu setting |

## 24. Bảng cluster_version
| Tên trường | Kiểu dữ liệu và độ dài | Nullable | Unique | P/F Key | Mặc định | Mô tả |
|------------|------------------------|----------|---------|---------|-----------|--------|
| id | BIGINT | | | P | | ID của phiên bản cluster |
| repo_version_id | BIGINT | | | F | | ID của phiên bản repo |
| cluster_id | BIGINT | | | F | | ID của cluster |
| state | VARCHAR(32) | | | | | Trạng thái |
| start_time | BIGINT | | | | | Thời gian bắt đầu |
| end_time | BIGINT | | | | | Thời gian kết thúc |
| user_name | VARCHAR(32) | | | | | Tên người dùng |

## 25. Bảng repo_version
| Tên trường | Kiểu dữ liệu và độ dài | Nullable | Unique | P/F Key | Mặc định | Mô tả |
|------------|------------------------|----------|---------|---------|-----------|--------|
| repo_version_id | BIGINT | | | P | | ID của phiên bản repo |
| stack_id | BIGINT | | | F | | ID của stack |
| version | VARCHAR(255) | | | | | Số phiên bản |
| display_name | VARCHAR(128) | | | | | Tên hiển thị |
| repositories | TEXT | | | | | Các repository |
| repo_type | VARCHAR(255) | | | | | Loại repo |
| version_url | VARCHAR(1024) | | | | | URL phiên bản |
| version_xml | TEXT | | | | | XML phiên bản |
| version_xsd | VARCHAR(512) | | | | | XSD phiên bản |
| parent_id | BIGINT | | | F | | ID của parent |

## 26. Bảng clusterconfig
| Tên trường | Kiểu dữ liệu và độ dài | Nullable | Unique | P/F Key | Mặc định | Mô tả |
|------------|------------------------|----------|---------|---------|-----------|--------|
| config_id | BIGINT | | | P | | ID của cấu hình |
| version_tag | VARCHAR(255) | | | | | Tag phiên bản |
| version | BIGINT | | | | | Số phiên bản |
| type_name | VARCHAR(255) | | | | | Tên loại |
| cluster_id | BIGINT | | | F | | ID của cluster |
| stack_id | BIGINT | | | F | | ID của stack |
| config_data | TEXT | | | | | Dữ liệu cấu hình |
| config_attributes | TEXT | | | | | Thuộc tính cấu hình |
| create_timestamp | BIGINT | | | | | Thời gian tạo |

## 27. Bảng clusterconfigmapping
| Tên trường | Kiểu dữ liệu và độ dài | Nullable | Unique | P/F Key | Mặc định | Mô tả |
|------------|------------------------|----------|---------|---------|-----------|--------|
| cluster_id | BIGINT | | | P,F | | ID của cluster |
| type_name | VARCHAR(255) | | | P | | Tên loại |
| version_tag | VARCHAR(255) | | | | | Tag phiên bản |
| create_timestamp | BIGINT | | | | | Thời gian tạo |
| selected | INTEGER | | | | | Đã được chọn |
| user_name | VARCHAR(255) | | | | | Tên người dùng |

## 28. Bảng clusterhostmapping
| Tên trường | Kiểu dữ liệu và độ dài | Nullable | Unique | P/F Key | Mặc định | Mô tả |
|------------|------------------------|----------|---------|---------|-----------|--------|
| cluster_id | BIGINT | | | P,F | | ID của cluster |
| host_id | BIGINT | | | P,F | | ID của host |

## 29. Bảng hosts
| Tên trường | Kiểu dữ liệu và độ dài | Nullable | Unique | P/F Key | Mặc định | Mô tả |
|------------|------------------------|----------|---------|---------|-----------|--------|
| host_id | BIGINT | | | P | | ID của host |
| host_name | VARCHAR(255) | | | | | Tên host |
| cpu_count | INTEGER | | | | | Số lượng CPU |
| ph_cpu_count | INTEGER | | | | | Số lượng CPU vật lý |
| cpu_info | VARCHAR(255) | | | | | Thông tin CPU |
| discovery_status | VARCHAR(2000) | | | | | Trạng thái khám phá |
| host_attributes | VARCHAR(20000) | | | | | Thuộc tính host |
| ipv4 | VARCHAR(255) | | | | | Địa chỉ IPv4 |
| ipv6 | VARCHAR(255) | | | | | Địa chỉ IPv6 |
| public_host_name | VARCHAR(255) | | | | | Tên host public |
| last_registration_time | BIGINT | | | | | Thời gian đăng ký cuối |
| os_arch | VARCHAR(255) | | | | | Kiến trúc OS |
| os_info | VARCHAR(1000) | | | | | Thông tin OS |
| os_type | VARCHAR(255) | | | | | Loại OS |
| rack_info | VARCHAR(255) | | | | | Thông tin rack |
| total_mem | BIGINT | | | | | Tổng bộ nhớ |

## 30. Bảng upgrade
| Tên trường | Kiểu dữ liệu và độ dài | Nullable | Unique | P/F Key | Mặc định | Mô tả |
|------------|------------------------|----------|---------|---------|-----------|--------|
| upgrade_id | BIGINT | | | P | | ID của upgrade |
| cluster_id | BIGINT | | | F | | ID của cluster |
| request_id | BIGINT | | | F | | ID của request |
| from_version | VARCHAR(255) | | | | | Phiên bản nguồn |
| to_version | VARCHAR(255) | | | | | Phiên bản đích |
| direction | VARCHAR(255) | | | | | Hướng nâng cấp |
| upgrade_package | VARCHAR(255) | | | | | Gói nâng cấp |
| upgrade_type | VARCHAR(32) | | | | | Loại nâng cấp |
| skip_failures | SMALLINT | | | | | Bỏ qua lỗi |
| skip_sc_failures | SMALLINT | | | | | Bỏ qua lỗi SC |
| downgrade_allowed | SMALLINT | | | | | Cho phép hạ cấp |
| suspended | SMALLINT | | | | | Đã tạm dừng |

## 31. Bảng clusterservices
| Tên trường | Kiểu dữ liệu và độ dài | Nullable | Unique | P/F Key | Mặc định | Mô tả |
|------------|------------------------|----------|---------|---------|-----------|--------|
| service_name | VARCHAR(255) | | | P | | Tên service |
| cluster_id | BIGINT | | | P,F | | ID của cluster |
| service_enabled | INTEGER | | | | | Service được kích hoạt |

## 32. Bảng clusterstate
| Tên trường | Kiểu dữ liệu và độ dài | Nullable | Unique | P/F Key | Mặc định | Mô tả |
|------------|------------------------|----------|---------|---------|-----------|--------|
| cluster_id | BIGINT | | | P,F | | ID của cluster |
| current_cluster_state | VARCHAR(255) | | | | | Trạng thái hiện tại của cluster |
| current_stack_id | BIGINT | | | F | | ID của stack hiện tại |

## 33. Bảng confgroupclusterconfigmapping
| Tên trường | Kiểu dữ liệu và độ dài | Nullable | Unique | P/F Key | Mặc định | Mô tả |
|------------|------------------------|----------|---------|---------|-----------|--------|
| config_group_id | BIGINT | | | P,F | | ID của nhóm cấu hình |
| cluster_id | BIGINT | | | F | | ID của cluster |
| config_type | VARCHAR(255) | | | | | Loại cấu hình |
| version_tag | VARCHAR(255) | | | | | Tag phiên bản |
| user_name | VARCHAR(255) | | | | | Tên người dùng |
| create_timestamp | BIGINT | | | | | Thời gian tạo |

## 34. Bảng configgroup
| Tên trường | Kiểu dữ liệu và độ dài | Nullable | Unique | P/F Key | Mặc định | Mô tả |
|------------|------------------------|----------|---------|---------|-----------|--------|
| group_id | BIGINT | | | P | | ID của nhóm |
| cluster_id | BIGINT | | | F | | ID của cluster |
| group_name | VARCHAR(255) | | | | | Tên nhóm |
| tag | VARCHAR(1024) | | | | | Tag |
| description | VARCHAR(1024) | | | | | Mô tả |
| create_timestamp | BIGINT | | | | | Thời gian tạo |
| service_name | VARCHAR(255) | | | | | Tên service |

## 35. Bảng configgrouphostmapping
| Tên trường | Kiểu dữ liệu và độ dài | Nullable | Unique | P/F Key | Mặc định | Mô tả |
|------------|------------------------|----------|---------|---------|-----------|--------|
| config_group_id | BIGINT | | | P,F | | ID của nhóm cấu hình |
| host_id | BIGINT | | | P,F | | ID của host |

## 36. Bảng host_role_command
| Tên trường | Kiểu dữ liệu và độ dài | Nullable | Unique | P/F Key | Mặc định | Mô tả |
|------------|------------------------|----------|---------|---------|-----------|--------|
| task_id | BIGINT | | | P | | ID của task |
| attempt_count | SMALLINT | | | | | Số lần thử |
| retry_allowed | SMALLINT | | | | | Cho phép thử lại |
| event | VARCHAR(32000) | | | | | Sự kiện |
| exitcode | INTEGER | | | | | Mã thoát |
| host_id | BIGINT | | | F | | ID của host |
| last_attempt_time | BIGINT | | | | | Thời gian thử cuối |
| request_id | BIGINT | | | F | | ID của request |
| role | VARCHAR(255) | | | | | Vai trò |
| stage_id | BIGINT | | | F | | ID của stage |
| start_time | BIGINT | | | | | Thời gian bắt đầu |
| original_start_time | BIGINT | | | | | Thời gian bắt đầu ban đầu |
| end_time | BIGINT | | | | | Thời gian kết thúc |
| status | VARCHAR(255) | | | | | Trạng thái |
| auto_skip_on_failure | SMALLINT | | | | | Tự động bỏ qua khi lỗi |
| std_error | BYTEA | | | | | Lỗi chuẩn |
| std_out | BYTEA | | | | | Đầu ra chuẩn |
| output_log | VARCHAR(255) | | | | | Log đầu ra |
| error_log | VARCHAR(255) | | | | | Log lỗi |
| structured_out | BYTEA | | | | | Đầu ra có cấu trúc |
| role_command | VARCHAR(255) | | | | | Lệnh vai trò |
| command_detail | VARCHAR(255) | | | | | Chi tiết lệnh |
| custom_command_name | VARCHAR(255) | | | | | Tên lệnh tùy chỉnh |

## 37. Bảng execution_command
| Tên trường | Kiểu dữ liệu và độ dài | Nullable | Unique | P/F Key | Mặc định | Mô tả |
|------------|------------------------|----------|---------|---------|-----------|--------|
| command | BYTEA | | | | | Lệnh thực thi |
| task_id | BIGINT | | | P,F | | ID của task |

## 38. Bảng extension
| Tên trường | Kiểu dữ liệu và độ dài | Nullable | Unique | P/F Key | Mặc định | Mô tả |
|------------|------------------------|----------|---------|---------|-----------|--------|
| extension_id | BIGINT | | | P | | ID của extension |
| extension_name | VARCHAR(255) | | | | | Tên extension |
| extension_version | VARCHAR(255) | | | | | Phiên bản extension |

## 39. Bảng extensionlink
| Tên trường | Kiểu dữ liệu và độ dài | Nullable | Unique | P/F Key | Mặc định | Mô tả |
|------------|------------------------|----------|---------|---------|-----------|--------|
| link_id | BIGINT | | | P | | ID của liên kết |
| stack_id | BIGINT | | | F | | ID của stack |
| extension_id | BIGINT | | | F | | ID của extension |

## 40. Bảng groups
| Tên trường | Kiểu dữ liệu và độ dài | Nullable | Unique | P/F Key | Mặc định | Mô tả |
|------------|------------------------|----------|---------|---------|-----------|--------|
| group_id | INTEGER | | | P | | ID của nhóm |
| principal_id | BIGINT | | | F | | ID của principal |
| group_name | VARCHAR(255) | | | | | Tên nhóm |
| ldap_group | INTEGER | | | | | Nhóm LDAP |


## 1. Bảng stage
| Tên trường | Kiểu dữ liệu và độ dài | Nullable | Unique | P/F Key | Mặc định | Mô tả |
|------------|------------------------|----------|---------|---------|-----------|--------|
| stage_id | BIGINT | X |  | P |  | ID của stage |
| request_id | BIGINT | X |  | F |  | ID của request |
| cluster_id | BIGINT | X |  | F |  | ID của cluster |
| skippable | SMALLINT |  |  |  |  | Có thể bỏ qua hay không |
| supports_auto_skip_failure | SMALLINT |  |  |  |  | Hỗ trợ tự động bỏ qua lỗi |
| log_info | CHARACTER VARYING(255) |  |  |  |  | Thông tin log |
| request_context | CHARACTER VARYING(255) |  |  |  |  | Context của request |
| cluster_host_info | BYTEA |  |  |  |  | Thông tin host của cluster |
| command_params | BYTEA |  |  |  |  | Tham số lệnh |
| host_params | BYTEA |  |  |  |  | Tham số host |

2. Bảng host_version
| Tên trường | Kiểu dữ liệu và độ dài | Nullable | Unique | P/F Key | Mặc định | Mô tả |
|------------|------------------------|----------|---------|---------|-----------|--------|
| id | BIGINT | X |  | P |  | ID của host version |
| repo_version_id | BIGINT | X |  | F |  | ID của repo version |
| host_id | BIGINT | X |  | F |  | ID của host |
| state | CHARACTER VARYING(32) |  |  |  |  | Trạng thái |

3. Bảng hostcomponentdesiredstate
| Tên trường | Kiểu dữ liệu và độ dài | Nullable | Unique | P/F Key | Mặc định | Mô tả |
|------------|------------------------|----------|---------|---------|-----------|--------|
| cluster_id | BIGINT | X |  | P |  | ID của cluster |
| component_name | CHARACTER VARYING(255) | X |  | P |  | Tên component |
| desired_stack_id | BIGINT | X |  | F |  | ID của stack mong muốn |
| desired_state | CHARACTER VARYING(255) |  |  |  |  | Trạng thái mong muốn |
| host_id | BIGINT | X |  | F |  | ID của host |
| service_name | CHARACTER VARYING(255) | X |  |  |  | Tên service |
| admin_state | CHARACTER VARYING(32) |  |  |  |  | Trạng thái admin |
| maintenance_state | CHARACTER VARYING(32) |  |  |  |  | Trạng thái bảo trì |
| security_state | CHARACTER VARYING(32) |  |  |  |  | Trạng thái bảo mật |
| restart_required | SMALLINT |  |  |  |  | Yêu cầu khởi động lại |

4. Bảng servicecomponentdesiredstate
| Tên trường | Kiểu dữ liệu và độ dài | Nullable | Unique | P/F Key | Mặc định | Mô tả |
|------------|------------------------|----------|---------|---------|-----------|--------|
| id | BIGINT | X |  | P |  | ID của desired state |
| component_name | CHARACTER VARYING(255) | X |  |  |  | Tên component |
| cluster_id | BIGINT | X |  | F |  | ID của cluster |
| desired_stack_id | BIGINT | X |  | F |  | ID của stack mong muốn |
| desired_version | CHARACTER VARYING(255) |  |  |  |  | Version mong muốn |
| desired_state | CHARACTER VARYING(255) |  |  |  |  | Trạng thái mong muốn |
| service_name | CHARACTER VARYING(255) | X |  |  |  | Tên service |
| recovery_enabled | SMALLINT |  |  |  |  | Cho phép phục hồi |

Tôi sẽ tiếp tục với các bảng còn lại:

5. Bảng hostcomponentstate
| Tên trường | Kiểu dữ liệu và độ dài | Nullable | Unique | P/F Key | Mặc định | Mô tả |
|------------|------------------------|----------|---------|---------|-----------|--------|
| id | BIGINT | X |  | P |  | ID của component state |
| cluster_id | BIGINT | X |  | F |  | ID của cluster |
| component_name | CHARACTER VARYING(255) | X |  |  |  | Tên component |
| version | CHARACTER VARYING(32) |  |  |  |  | Phiên bản |
| current_stack_id | BIGINT | X |  | F |  | ID của stack hiện tại |
| current_state | CHARACTER VARYING(255) |  |  |  |  | Trạng thái hiện tại |
| host_id | BIGINT | X |  | F |  | ID của host |
| service_name | CHARACTER VARYING(255) | X |  |  |  | Tên service |
| upgrade_state | CHARACTER VARYING(32) |  |  |  |  | Trạng thái nâng cấp |
| security_state | CHARACTER VARYING(32) |  |  |  |  | Trạng thái bảo mật |

6. Bảng hostconfigmapping
| Tên trường | Kiểu dữ liệu và độ dài | Nullable | Unique | P/F Key | Mặc định | Mô tả |
|------------|------------------------|----------|---------|---------|-----------|--------|
| cluster_id | BIGINT | X |  | P |  | ID của cluster |
| host_id | BIGINT | X |  | P |  | ID của host |
| type_name | CHARACTER VARYING(255) | X |  | P |  | Tên loại |
| version_tag | CHARACTER VARYING(255) | X |  |  |  | Tag phiên bản |
| service_name | CHARACTER VARYING(255) |  |  |  |  | Tên service |
| create_timestamp | BIGINT |  |  |  |  | Thời gian tạo |
| selected | INTEGER |  |  |  |  | Đã chọn |
| user_name | CHARACTER VARYING(255) |  |  |  |  | Tên người dùng |

7. Bảng hostgroup
| Tên trường | Kiểu dữ liệu và độ dài | Nullable | Unique | P/F Key | Mặc định | Mô tả |
|------------|------------------------|----------|---------|---------|-----------|--------|
| blueprint_name | CHARACTER VARYING(255) | X |  | P |  | Tên blueprint |
| name | CHARACTER VARYING(255) | X |  | P |  | Tên nhóm host |
| cardinality | CHARACTER VARYING(255) |  |  |  |  | Số lượng |

8. Bảng hostgroup_component
| Tên trường | Kiểu dữ liệu và độ dài | Nullable | Unique | P/F Key | Mặc định | Mô tả |
|------------|------------------------|----------|---------|---------|-----------|--------|
| blueprint_name | CHARACTER VARYING(255) | X |  | P |  | Tên blueprint |
| hostgroup_name | CHARACTER VARYING(255) | X |  | P |  | Tên nhóm host |
| name | CHARACTER VARYING(255) | X |  | P |  | Tên component |
| provision_action | CHARACTER VARYING(255) |  |  |  |  | Hành động cung cấp |

9. Bảng hostgroup_configuration
| Tên trường | Kiểu dữ liệu và độ dài | Nullable | Unique | P/F Key | Mặc định | Mô tả |
|------------|------------------------|----------|---------|---------|-----------|--------|
| blueprint_name | CHARACTER VARYING(255) | X |  | P |  | Tên blueprint |
| hostgroup_name | CHARACTER VARYING(255) | X |  | P |  | Tên nhóm host |
| type_name | CHARACTER VARYING(255) | X |  | P |  | Tên loại |
| config_data | TEXT |  |  |  |  | Dữ liệu cấu hình |
| config_attributes | TEXT |  |  |  |  | Thuộc tính cấu hình |

10. Bảng hoststate
| Tên trường | Kiểu dữ liệu và độ dài | Nullable | Unique | P/F Key | Mặc định | Mô tả |
|------------|------------------------|----------|---------|---------|-----------|--------|
| agent_version | CHARACTER VARYING(255) |  |  |  |  | Phiên bản agent |
| available_mem | BIGINT |  |  |  |  | Bộ nhớ khả dụng |
| current_state | CHARACTER VARYING(255) |  |  |  |  | Trạng thái hiện tại |
| health_status | CHARACTER VARYING(255) |  |  |  |  | Tình trạng sức khỏe |
| host_id | BIGINT | X |  | P |  | ID của host |
| time_in_state | BIGINT |  |  |  |  | Thời gian trong trạng thái |
| maintenance_state | CHARACTER VARYING(512) |  |  |  |  | Trạng thái bảo trì |

11. Bảng kerberos_descriptor
| Tên trường | Kiểu dữ liệu và độ dài | Nullable | Unique | P/F Key | Mặc định | Mô tả |
|------------|------------------------|----------|---------|---------|-----------|--------|
| kerberos_descriptor_name | CHARACTER VARYING(255) | X |  | P |  | Tên mô tả Kerberos |
| kerberos_descriptor | TEXT |  |  |  |  | Mô tả Kerberos |

12. Bảng kerberos_principal
| Tên trường | Kiểu dữ liệu và độ dài | Nullable | Unique | P/F Key | Mặc định | Mô tả |
|------------|------------------------|----------|---------|---------|-----------|--------|
| principal_name | CHARACTER VARYING(255) | X |  | P |  | Tên principal |
| is_service | SMALLINT |  |  |  |  | Là service |
| cached_keytab_path | CHARACTER VARYING(255) |  |  |  |  | Đường dẫn keytab cache |

13. Bảng kerberos_principal_host
| Tên trường | Kiểu dữ liệu và độ dài | Nullable | Unique | P/F Key | Mặc định | Mô tả |
|------------|------------------------|----------|---------|---------|-----------|--------|
| principal_name | CHARACTER VARYING(255) | X |  | P |  | Tên principal |
| host_id | BIGINT | X |  | P |  | ID của host |

14. Bảng key_value_store
| Tên trường | Kiểu dữ liệu và độ dài | Nullable | Unique | P/F Key | Mặc định | Mô tả |
|------------|------------------------|----------|---------|---------|-----------|--------|
| key | CHARACTER VARYING(255) | X |  | P |  | Khóa |
| value | CHARACTER VARYING |  |  |  |  | Giá trị |

15. Bảng members
| Tên trường | Kiểu dữ liệu và độ dài | Nullable | Unique | P/F Key | Mặc định | Mô tả |
|------------|------------------------|----------|---------|---------|-----------|--------|
| member_id | INTEGER | X |  | P |  | ID của thành viên |
| group_id | INTEGER | X |  | F |  | ID của nhóm |
| user_id | INTEGER | X |  | F |  | ID của người dùng |

16. Bảng users
| Tên trường | Kiểu dữ liệu và độ dài | Nullable | Unique | P/F Key | Mặc định | Mô tả |
|------------|------------------------|----------|---------|---------|-----------|--------|
| user_id | INTEGER | X |  | P |  | ID của người dùng |
| principal_id | BIGINT | X |  | F |  | ID của principal |
| ldap_user | INTEGER |  |  |  |  | Người dùng LDAP |
| user_name | CHARACTER VARYING(255) | X |  |  |  | Tên người dùng |
| user_type | CHARACTER VARYING(255) |  |  |  |  | Loại người dùng |
| create_time | TIMESTAMP(6) |  |  |  |  | Thời gian tạo |
| user_password | CHARACTER VARYING(255) |  |  |  |  | Mật khẩu |
| active | INTEGER |  |  |  |  | Trạng thái hoạt động |
| active_widget_layouts | CHARACTER VARYING(1024) |  |  |  |  | Layout widget đang hoạt động |

17. Bảng metainfo
| Tên trường | Kiểu dữ liệu và độ dài | Nullable | Unique | P/F Key | Mặc định | Mô tả |
|------------|------------------------|----------|---------|---------|-----------|--------|
| metainfo_key | CHARACTER VARYING(255) | X |  | P |  | Khóa metainfo |
| metainfo_value | CHARACTER VARYING |  |  |  |  | Giá trị metainfo |

18. Bảng permission_roleauthorization
| Tên trường | Kiểu dữ liệu và độ dài | Nullable | Unique | P/F Key | Mặc định | Mô tả |
|------------|------------------------|----------|---------|---------|-----------|--------|
| permission_id | BIGINT | X |  | P |  | ID của quyền |
| authorization_id | CHARACTER VARYING(100) | X |  | P |  | ID của ủy quyền |

19. Bảng roleauthorization
| Tên trường | Kiểu dữ liệu và độ dài | Nullable | Unique | P/F Key | Mặc định | Mô tả |
|------------|------------------------|----------|---------|---------|-----------|--------|
| authorization_id | CHARACTER VARYING(100) | X |  | P |  | ID của ủy quyền |
| authorization_name | CHARACTER VARYING(255) |  |  |  |  | Tên ủy quyền |

## 20. Bảng qrtz_triggers
| Tên trường | Kiểu dữ liệu và độ dài | Nullable | Unique | P/F Key | Mặc định | Mô tả |
|------------|------------------------|----------|---------|---------|-----------|--------|
| sched_name | CHARACTER VARYING(120) | X |  | P |  | Tên lịch |
| trigger_name | CHARACTER VARYING(200) | X |  | P |  | Tên trigger |
| trigger_group | CHARACTER VARYING(200) | X |  | P |  | Nhóm trigger |
| job_name | CHARACTER VARYING(200) | X |  | F |  | Tên job |
| job_group | CHARACTER VARYING(200) | X |  | F |  | Nhóm job |
| description | CHARACTER VARYING(250) |  |  |  |  | Mô tả |
| next_fire_time | BIGINT |  |  |  |  | Thời gian kích hoạt tiếp theo |
| prev_fire_time | BIGINT |  |  |  |  | Thời gian kích hoạt trước đó |
| priority | INTEGER |  |  |  |  | Độ ưu tiên |
| trigger_state | CHARACTER VARYING(16) |  |  |  |  | Trạng thái trigger |
| trigger_type | CHARACTER VARYING(8) |  |  |  |  | Loại trigger |
| start_time | BIGINT |  |  |  |  | Thời gian bắt đầu |
| end_time | BIGINT |  |  |  |  | Thời gian kết thúc |
| calendar_name | CHARACTER VARYING(200) |  |  |  |  | Tên lịch |
| misfire_instr | SMALLINT |  |  |  |  | Hướng dẫn khi bỏ lỡ |
| job_data | BYTEA |  |  |  |  | Dữ liệu job |

21. Bảng qrtz_blob_triggers
| Tên trường | Kiểu dữ liệu và độ dài | Nullable | Unique | P/F Key | Mặc định | Mô tả |
|------------|------------------------|----------|---------|---------|-----------|--------|
| sched_name | CHARACTER VARYING(120) | X |  | P |  | Tên lịch |
| trigger_name | CHARACTER VARYING(200) | X |  | P |  | Tên trigger |
| trigger_group | CHARACTER VARYING(200) | X |  | P |  | Nhóm trigger |
| blob_data | BYTEA |  |  |  |  | Dữ liệu blob |

22. Bảng qrtz_calendars
| Tên trường | Kiểu dữ liệu và độ dài | Nullable | Unique | P/F Key | Mặc định | Mô tả |
|------------|------------------------|----------|---------|---------|-----------|--------|
| sched_name | CHARACTER VARYING(120) | X |  | P |  | Tên lịch |
| calendar_name | CHARACTER VARYING(200) | X |  | P |  | Tên lịch |
| calendar | BYTEA |  |  |  |  | Dữ liệu lịch |


1. Bảng qrtz_cron_triggers
| Tên trường | Kiểu dữ liệu và độ dài | Nullable | Unique | P/F Key | Mặc định | Mô tả |
|------------|------------------------|----------|---------|---------|-----------|--------|
| sched_name | CHARACTER VARYING(120) | X |  | P |  | Tên lịch |
| trigger_name | CHARACTER VARYING(200) | X |  | P |  | Tên trigger |
| trigger_group | CHARACTER VARYING(200) | X |  | P |  | Nhóm trigger |
| cron_expression | CHARACTER VARYING(120) |  |  |  |  | Biểu thức cron |
| time_zone_id | CHARACTER VARYING(80) |  |  |  |  | ID múi giờ |

2. Bảng qrtz_fired_triggers
| Tên trường | Kiểu dữ liệu và độ dài | Nullable | Unique | P/F Key | Mặc định | Mô tả |
|------------|------------------------|----------|---------|---------|-----------|--------|
| sched_name | CHARACTER VARYING(120) | X |  | P |  | Tên lịch |
| entry_id | CHARACTER VARYING(95) | X |  | P |  | ID entry |
| trigger_name | CHARACTER VARYING(200) | X |  |  |  | Tên trigger |
| trigger_group | CHARACTER VARYING(200) | X |  |  |  | Nhóm trigger |
| instance_name | CHARACTER VARYING(200) | X |  |  |  | Tên instance |
| fired_time | BIGINT |  |  |  |  | Thời gian kích hoạt |
| sched_time | BIGINT |  |  |  |  | Thời gian lên lịch |
| priority | INTEGER |  |  |  |  | Độ ưu tiên |
| state | CHARACTER VARYING(16) |  |  |  |  | Trạng thái |
| job_name | CHARACTER VARYING(200) |  |  |  |  | Tên job |
| job_group | CHARACTER VARYING(200) |  |  |  |  | Nhóm job |
| is_nonconcurrent | BOOLEAN |  |  |  |  | Không đồng thời |
| requests_recovery | BOOLEAN |  |  |  |  | Yêu cầu khôi phục |

3. Bảng qrtz_job_details
| Tên trường | Kiểu dữ liệu và độ dài | Nullable | Unique | P/F Key | Mặc định | Mô tả |
|------------|------------------------|----------|---------|---------|-----------|--------|
| sched_name | CHARACTER VARYING(120) | X |  | P |  | Tên lịch |
| job_name | CHARACTER VARYING(200) | X |  | P |  | Tên job |
| job_group | CHARACTER VARYING(200) | X |  | P |  | Nhóm job |
| description | CHARACTER VARYING(250) |  |  |  |  | Mô tả |
| job_class_name | CHARACTER VARYING(250) |  |  |  |  | Tên lớp job |
| is_durable | BOOLEAN |  |  |  |  | Bền vững |
| is_nonconcurrent | BOOLEAN |  |  |  |  | Không đồng thời |
| is_update_data | BOOLEAN |  |  |  |  | Cập nhật dữ liệu |
| requests_recovery | BOOLEAN |  |  |  |  | Yêu cầu khôi phục |
| job_data | BYTEA |  |  |  |  | Dữ liệu job |

4. Bảng qrtz_locks
| Tên trường | Kiểu dữ liệu và độ dài | Nullable | Unique | P/F Key | Mặc định | Mô tả |
|------------|------------------------|----------|---------|---------|-----------|--------|
| sched_name | CHARACTER VARYING(120) | X |  | P |  | Tên lịch |
| lock_name | CHARACTER VARYING(40) | X |  | P |  | Tên khóa |

5. Bảng qrtz_paused_trigger_grps
| Tên trường | Kiểu dữ liệu và độ dài | Nullable | Unique | P/F Key | Mặc định | Mô tả |
|------------|------------------------|----------|---------|---------|-----------|--------|
| sched_name | CHARACTER VARYING(120) | X |  | P |  | Tên lịch |
| trigger_group | CHARACTER VARYING(200) | X |  | P |  | Nhóm trigger |

Tôi sẽ tiếp tục với các bảng còn lại:

6. Bảng qrtz_scheduler_state
| Tên trường | Kiểu dữ liệu và độ dài | Nullable | Unique | P/F Key | Mặc định | Mô tả |
|------------|------------------------|----------|---------|---------|-----------|--------|
| sched_name | CHARACTER VARYING(120) | X |  | P |  | Tên lịch |
| instance_name | CHARACTER VARYING(200) | X |  | P |  | Tên instance |
| last_checkin_time | BIGINT |  |  |  |  | Thời gian check-in cuối |
| checkin_interval | BIGINT |  |  |  |  | Khoảng thời gian check-in |

7. Bảng qrtz_simple_triggers
| Tên trường | Kiểu dữ liệu và độ dài | Nullable | Unique | P/F Key | Mặc định | Mô tả |
|------------|------------------------|----------|---------|---------|-----------|--------|
| sched_name | CHARACTER VARYING(120) | X |  | P |  | Tên lịch |
| trigger_name | CHARACTER VARYING(200) | X |  | P |  | Tên trigger |
| trigger_group | CHARACTER VARYING(200) | X |  | P |  | Nhóm trigger |
| repeat_count | BIGINT |  |  |  |  | Số lần lặp lại |
| repeat_interval | BIGINT |  |  |  |  | Khoảng thời gian lặp |
| times_triggered | BIGINT |  |  |  |  | Số lần đã kích hoạt |

8. Bảng qrtz_simprop_triggers
| Tên trường | Kiểu dữ liệu và độ dài | Nullable | Unique | P/F Key | Mặc định | Mô tả |
|------------|------------------------|----------|---------|---------|-----------|--------|
| sched_name | CHARACTER VARYING(120) | X |  | P |  | Tên lịch |
| trigger_name | CHARACTER VARYING(200) | X |  | P |  | Tên trigger |
| trigger_group | CHARACTER VARYING(200) | X |  | P |  | Nhóm trigger |
| str_prop_1 | CHARACTER VARYING(512) |  |  |  |  | Thuộc tính chuỗi 1 |
| str_prop_2 | CHARACTER VARYING(512) |  |  |  |  | Thuộc tính chuỗi 2 |
| str_prop_3 | CHARACTER VARYING(512) |  |  |  |  | Thuộc tính chuỗi 3 |
| int_prop_1 | INTEGER |  |  |  |  | Thuộc tính số nguyên 1 |
| int_prop_2 | INTEGER |  |  |  |  | Thuộc tính số nguyên 2 |
| long_prop_1 | BIGINT |  |  |  |  | Thuộc tính long 1 |
| long_prop_2 | BIGINT |  |  |  |  | Thuộc tính long 2 |
| dec_prop_1 | NUMERIC(13,4) |  |  |  |  | Thuộc tính decimal 1 |
| dec_prop_2 | NUMERIC(13,4) |  |  |  |  | Thuộc tính decimal 2 |
| bool_prop_1 | BOOLEAN |  |  |  |  | Thuộc tính boolean 1 |
| bool_prop_2 | BOOLEAN |  |  |  |  | Thuộc tính boolean 2 |

9. Bảng remoteambaricluster
| Tên trường | Kiểu dữ liệu và độ dài | Nullable | Unique | P/F Key | Mặc định | Mô tả |
|------------|------------------------|----------|---------|---------|-----------|--------|
| cluster_id | BIGINT | X |  | P |  | ID của cluster |
| name | CHARACTER VARYING(255) | X |  |  |  | Tên cluster |
| username | CHARACTER VARYING(255) |  |  |  |  | Tên người dùng |
| url | CHARACTER VARYING(255) |  |  |  |  | URL |
| password | CHARACTER VARYING(255) |  |  |  |  | Mật khẩu |

10. Bảng remoteambariclusterservice
| Tên trường | Kiểu dữ liệu và độ dài | Nullable | Unique | P/F Key | Mặc định | Mô tả |
|------------|------------------------|----------|---------|---------|-----------|--------|
| id | BIGINT | X |  | P |  | ID của service |
| cluster_id | BIGINT | X |  | F |  | ID của cluster |
| service_name | CHARACTER VARYING(255) | X |  |  |  | Tên service |

11. Bảng requestschedule
| Tên trường | Kiểu dữ liệu và độ dài | Nullable | Unique | P/F Key | Mặc định | Mô tả |
|------------|------------------------|----------|---------|---------|-----------|--------|
| schedule_id | BIGINT | X |  | P |  | ID của lịch |
| cluster_id | BIGINT | X |  | F |  | ID của cluster |
| description | CHARACTER VARYING(255) |  |  |  |  | Mô tả |
| status | CHARACTER VARYING(255) |  |  |  |  | Trạng thái |
| batch_separation_seconds | SMALLINT |  |  |  |  | Thời gian giãn cách batch |
| batch_toleration_limit | SMALLINT |  |  |  |  | Giới hạn chịu đựng batch |
| authenticated_user_id | INTEGER |  |  |  |  | ID người dùng xác thực |
| create_user | CHARACTER VARYING(255) |  |  |  |  | Người tạo |
| create_timestamp | BIGINT |  |  |  |  | Thời gian tạo |
| update_user | CHARACTER VARYING(255) |  |  |  |  | Người cập nhật |
| update_timestamp | BIGINT |  |  |  |  | Thời gian cập nhật |
| minutes | CHARACTER VARYING(10) |  |  |  |  | Phút |
| hours | CHARACTER VARYING(10) |  |  |  |  | Giờ |
| days_of_month | CHARACTER VARYING(10) |  |  |  |  | Ngày trong tháng |
| month | CHARACTER VARYING(10) |  |  |  |  | Tháng |
| day_of_week | CHARACTER VARYING(10) |  |  |  |  | Ngày trong tuần |
| yeartoschedule | CHARACTER VARYING(10) |  |  |  |  | Năm để lên lịch |
| starttime | CHARACTER VARYING(50) |  |  |  |  | Thời gian bắt đầu |
| endtime | CHARACTER VARYING(50) |  |  |  |  | Thời gian kết thúc |
| last_execution_status | CHARACTER VARYING(255) |  |  |  |  | Trạng thái thực thi cuối |

12. Bảng request
| Tên trường | Kiểu dữ liệu và độ dài | Nullable | Unique | P/F Key | Mặc định | Mô tả |
|------------|------------------------|----------|---------|---------|-----------|--------|
| request_id | BIGINT | X |  | P |  | ID của request |
| cluster_id | BIGINT | X |  | F |  | ID của cluster |
| command_name | CHARACTER VARYING(255) |  |  |  |  | Tên lệnh |
| create_time | BIGINT |  |  |  |  | Thời gian tạo |
| end_time | BIGINT |  |  |  |  | Thời gian kết thúc |
| exclusive_execution | SMALLINT |  |  |  |  | Thực thi độc quyền |
| inputs | BYTEA |  |  |  |  | Đầu vào |
| request_context | CHARACTER VARYING(255) |  |  |  |  | Context của request |
| request_type | CHARACTER VARYING(255) |  |  |  |  | Loại request |
| request_schedule_id | BIGINT |  |  | F |  | ID của lịch request |
| start_time | BIGINT |  |  |  |  | Thời gian bắt đầu |
| status | CHARACTER VARYING(255) |  |  |  |  | Trạng thái |

### Bảng requestoperationlevel
| Tên trường | Kiểu dữ liệu và độ dài | Nullable | Unique | P/F Key | Mặc định | Mô tả |
|------------|------------------------|----------|---------|---------|-----------|--------|
| operation_level_id | BIGINT | X |  | P |  | ID của operation level |
| request_id | BIGINT | X |  | F |  | ID của request |
| level_name | CHARACTER VARYING(255) |  |  |  |  | Tên level |
| cluster_name | CHARACTER VARYING(255) |  |  |  |  | Tên cluster |
| service_name | CHARACTER VARYING(255) |  |  |  |  | Tên service |
| host_component_name | CHARACTER VARYING(255) |  |  |  |  | Tên host component |
| host_id | BIGINT |  |  | F |  | ID của host |

### Bảng requestresourcefilter
| Tên trường | Kiểu dữ liệu và độ dài | Nullable | Unique | P/F Key | Mặc định | Mô tả |
|------------|------------------------|----------|---------|---------|-----------|--------|
| filter_id | BIGINT | X |  | P |  | ID của filter |
| request_id | BIGINT | X |  | F |  | ID của request |
| service_name | CHARACTER VARYING(255) |  |  |  |  | Tên service |
| component_name | CHARACTER VARYING(255) |  |  |  |  | Tên component |
| hosts | BYTEA |  |  |  |  | Thông tin hosts |

### Bảng requestschedulebatchrequest
| Tên trường | Kiểu dữ liệu và độ dài | Nullable | Unique | P/F Key | Mặc định | Mô tả |
|------------|------------------------|----------|---------|---------|-----------|--------|
| schedule_id | BIGINT | X |  | P |  | ID của schedule |
| batch_id | BIGINT | X |  | P |  | ID của batch |
| request_id | BIGINT |  |  | F |  | ID của request |
| request_type | CHARACTER VARYING(255) |  |  |  |  | Loại request |
| request_uri | CHARACTER VARYING(1024) |  |  |  |  | URI của request |
| request_body | BYTEA |  |  |  |  | Body của request |
| request_status | CHARACTER VARYING(255) |  |  |  |  | Trạng thái request |
| return_code | SMALLINT |  |  |  |  | Mã trả về |
| return_message | CHARACTER VARYING(20000) |  |  |  |  | Thông điệp trả về |

### Bảng role_success_criteria
| Tên trường | Kiểu dữ liệu và độ dài | Nullable | Unique | P/F Key | Mặc định | Mô tả |
|------------|------------------------|----------|---------|---------|-----------|--------|
| role | CHARACTER VARYING(255) | X |  | P |  | Tên role |
| request_id | BIGINT | X |  | P |  | ID của request |
| stage_id | BIGINT | X |  | P |  | ID của stage |
| success_factor | DOUBLE PRECISION |  |  |  |  | Hệ số thành công |

### Bảng servicecomponent_history
| Tên trường | Kiểu dữ liệu và độ dài | Nullable | Unique | P/F Key | Mặc định | Mô tả |
|------------|------------------------|----------|---------|---------|-----------|--------|
| id | BIGINT | X |  | P |  | ID của history |
| component_id | BIGINT |  |  | F |  | ID của component |
| upgrade_id | BIGINT |  |  | F |  | ID của upgrade |
| from_stack_id | BIGINT |  |  | F |  | ID stack ban đầu |
| to_stack_id | BIGINT |  |  | F |  | ID stack đích |

### Bảng serviceconfig
| Tên trường | Kiểu dữ liệu và độ dài | Nullable | Unique | P/F Key | Mặc định | Mô tả |
|------------|------------------------|----------|---------|---------|-----------|--------|
| service_config_id | BIGINT | X |  | P |  | ID của service config |
| cluster_id | BIGINT | X |  | F |  | ID của cluster |
| service_name | CHARACTER VARYING(255) | X |  |  |  | Tên service |
| version | BIGINT | X |  |  |  | Phiên bản |
| create_timestamp | BIGINT |  |  |  |  | Thời gian tạo |
| stack_id | BIGINT |  |  | F |  | ID của stack |
| user_name | CHARACTER VARYING(255) |  |  |  |  | Tên người dùng |
| group_id | BIGINT |  |  | F |  | ID của group |
| note | TEXT |  |  |  |  | Ghi chú |

### Bảng serviceconfighosts
| Tên trường | Kiểu dữ liệu và độ dài | Nullable | Unique | P/F Key | Mặc định | Mô tả |
|------------|------------------------|----------|---------|---------|-----------|--------|
| service_config_id | BIGINT | X |  | P |  | ID của service config |
| host_id | BIGINT | X |  | P |  | ID của host |

### Bảng serviceconfigmapping
| Tên trường | Kiểu dữ liệu và độ dài | Nullable | Unique | P/F Key | Mặc định | Mô tả |
|------------|------------------------|----------|---------|---------|-----------|--------|
| service_config_id | BIGINT | X |  | P |  | ID của service config |
| config_id | BIGINT | X |  | P |  | ID của config |

### Bảng servicedesiredstate
| Tên trường | Kiểu dữ liệu và độ dài | Nullable | Unique | P/F Key | Mặc định | Mô tả |
|------------|------------------------|----------|---------|---------|-----------|--------|
| cluster_id | BIGINT | X |  | P |  | ID của cluster |
| desired_host_role_mapping | INTEGER |  |  |  |  | Mapping vai trò host mong muốn |
| desired_stack_id | BIGINT |  |  | F |  | ID stack mong muốn |
| desired_state | CHARACTER VARYING(255) |  |  |  |  | Trạng thái mong muốn |
| service_name | CHARACTER VARYING(255) | X |  | P |  | Tên service |
| maintenance_state | CHARACTER VARYING(32) |  |  |  |  | Trạng thái bảo trì |
| security_state | CHARACTER VARYING(32) |  |  |  |  | Trạng thái bảo mật |

### Bảng setting
| Tên trường | Kiểu dữ liệu và độ dài | Nullable | Unique | P/F Key | Mặc định | Mô tả |
|------------|------------------------|----------|---------|---------|-----------|--------|
| id | BIGINT | X |  | P |  | ID của setting |
| name | CHARACTER VARYING(255) | X |  |  |  | Tên setting |
| setting_type | CHARACTER VARYING(255) |  |  |  |  | Loại setting |
| content | TEXT |  |  |  |  | Nội dung |
| updated_by | CHARACTER VARYING(255) |  |  |  |  | Người cập nhật |
| update_timestamp | BIGINT |  |  |  |  | Thời gian cập nhật |

### Bảng topology_host_info
| Tên trường | Kiểu dữ liệu và độ dài | Nullable | Unique | P/F Key | Mặc định | Mô tả |
|------------|------------------------|----------|---------|---------|-----------|--------|
| id | BIGINT | X |  | P |  | ID của host info |
| group_id | BIGINT |  |  | F |  | ID của group |
| fqdn | CHARACTER VARYING(255) |  |  |  |  | FQDN của host |
| host_id | BIGINT |  |  | F |  | ID của host |
| host_count | INTEGER |  |  |  |  | Số lượng host |
| predicate | CHARACTER VARYING(2048) |  |  |  |  | Điều kiện |
| rack_info | CHARACTER VARYING(255) |  |  |  |  | Thông tin rack |

### Bảng topology_hostgroup
| Tên trường | Kiểu dữ liệu và độ dài | Nullable | Unique | P/F Key | Mặc định | Mô tả |
|------------|------------------------|----------|---------|---------|-----------|--------|
| id | BIGINT | X |  | P |  | ID của host group |
| name | CHARACTER VARYING(255) |  |  |  |  | Tên group |
| group_properties | TEXT |  |  |  |  | Thuộc tính group |
| group_attributes | TEXT |  |  |  |  | Thuộc tính bổ sung |
| request_id | BIGINT |  |  | F |  | ID của request |

### Bảng topology_host_request
| Tên trường | Kiểu dữ liệu và độ dài | Nullable | Unique | P/F Key | Mặc định | Mô tả |
|------------|------------------------|----------|---------|---------|-----------|--------|
| id | BIGINT | X |  | P |  | ID của host request |
| logical_request_id | BIGINT |  |  | F |  | ID của logical request |
| group_id | BIGINT |  |  | F |  | ID của group |
| stage_id | BIGINT |  |  | F |  | ID của stage |
| host_name | CHARACTER VARYING(255) |  |  |  |  | Tên host |

### Bảng topology_logical_request
| Tên trường | Kiểu dữ liệu và độ dài | Nullable | Unique | P/F Key | Mặc định | Mô tả |
|------------|------------------------|----------|---------|---------|-----------|--------|
| id | BIGINT | X |  | P |  | ID của logical request |
| request_id | BIGINT |  |  | F |  | ID của request |
| description | CHARACTER VARYING(1024) |  |  |  |  | Mô tả |

### Bảng topology_host_task
| Tên trường | Kiểu dữ liệu và độ dài | Nullable | Unique | P/F Key | Mặc định | Mô tả |
|------------|------------------------|----------|---------|---------|-----------|--------|
| id | BIGINT | X |  | P |  | ID của host task |
| host_request_id | BIGINT |  |  | F |  | ID của host request |
| type | CHARACTER VARYING(255) |  |  |  |  | Loại task |

### Bảng topology_request
| Tên trường | Kiểu dữ liệu và độ dài | Nullable | Unique | P/F Key | Mặc định | Mô tả |
|------------|------------------------|----------|---------|---------|-----------|--------|
| id | BIGINT | X |  | P |  | ID của request |
| action | CHARACTER VARYING(255) |  |  |  |  | Hành động |
| cluster_id | BIGINT |  |  | F |  | ID của cluster |
| bp_name | CHARACTER VARYING(100) |  |  |  |  | Tên blueprint |
| cluster_properties | TEXT |  |  |  |  | Thuộc tính cluster |
| cluster_attributes | TEXT |  |  |  |  | Thuộc tính bổ sung |
| description | CHARACTER VARYING(1024) |  |  |  |  | Mô tả |
| provision_action | CHARACTER VARYING(255) |  |  |  |  | Hành động cấp phát |

### Bảng upgrade_group
| Tên trường | Kiểu dữ liệu và độ dài | Nullable | Unique | P/F Key | Mặc định | Mô tả |
|------------|------------------------|----------|---------|---------|-----------|--------|
| upgrade_group_id | BIGINT | X |  | P |  | ID của upgrade group |
| upgrade_id | BIGINT | X |  | F |  | ID của upgrade |
| group_name | CHARACTER VARYING(255) |  |  |  |  | Tên group |
| group_title | CHARACTER VARYING(1024) |  |  |  |  | Tiêu đề group |

### Bảng upgrade_item
| Tên trường | Kiểu dữ liệu và độ dài | Nullable | Unique | P/F Key | Mặc định | Mô tả |
|------------|------------------------|----------|---------|---------|-----------|--------|
| upgrade_item_id | BIGINT | X |  | P |  | ID của upgrade item |
| upgrade_group_id | BIGINT | X |  | F |  | ID của upgrade group |
| stage_id | BIGINT |  |  | F |  | ID của stage |
| state | CHARACTER VARYING(255) |  |  |  |  | Trạng thái |
| hosts | TEXT |  |  |  |  | Danh sách hosts |
| tasks | TEXT |  |  |  |  | Danh sách tasks |
| item_text | CHARACTER VARYING(1024) |  |  |  |  | Nội dung item |

### Bảng users_1
| Tên trường | Kiểu dữ liệu và độ dài | Nullable | Unique | P/F Key | Mặc định | Mô tả |
|------------|------------------------|----------|---------|---------|-----------|--------|
| user_id | INTEGER | X |  | P |  | ID của user |
| principal_id | BIGINT |  |  | F |  | ID của principal |
| ldap_user | INTEGER |  |  |  |  | Người dùng LDAP |
| user_name | CHARACTER VARYING(255) |  |  |  |  | Tên người dùng |
| user_type | CHARACTER VARYING(255) |  |  |  |  | Loại người dùng |
| create_time | TIMESTAMP |  |  |  |  | Thời gian tạo |
| user_password | CHARACTER VARYING(255) |  |  |  |  | Mật khẩu |
| active

### Bảng users_2
| Tên trường | Kiểu dữ liệu và độ dài | Nullable | Unique | P/F Key | Mặc định | Mô tả |
|------------|------------------------|----------|---------|---------|-----------|--------|
| user_id | INTEGER | X |  | P |  | ID của user |
| principal_id | BIGINT |  |  | F |  | ID của principal |
| ldap_user | INTEGER |  |  |  |  | Người dùng LDAP |
| user_name | CHARACTER VARYING(255) |  |  |  |  | Tên người dùng |
| user_type | CHARACTER VARYING(255) |  |  |  |  | Loại người dùng |
| create_time | TIMESTAMP |  |  |  |  | Thời gian tạo |
| user_password | CHARACTER VARYING(255) |  |  |  |  | Mật khẩu |
| active | INTEGER |  |  |  |  | Trạng thái kích hoạt |
| active_widget_layouts | CHARACTER VARYING(1024) |  |  |  |  | Layout widget đang kích hoạt |

### Bảng viewinstance
| Tên trường | Kiểu dữ liệu và độ dài | Nullable | Unique | P/F Key | Mặc định | Mô tả |
|------------|------------------------|----------|---------|---------|-----------|--------|
| view_instance_id | BIGINT | X |  | P |  | ID của view instance |
| resource_id | BIGINT |  |  | F |  | ID của resource |
| view_name | CHARACTER VARYING(255) | X |  |  |  | Tên view |
| name | CHARACTER VARYING(255) | X |  |  |  | Tên instance |
| label | CHARACTER VARYING(255) |  |  |  |  | Nhãn |
| description | CHARACTER VARYING(2048) |  |  |  |  | Mô tả |
| visible | CHARACTER(1) |  |  |  |  | Trạng thái hiển thị |
| icon | CHARACTER VARYING(255) |  |  |  |  | Icon |
| icon64 | CHARACTER VARYING(255) |  |  |  |  | Icon 64px |
| xml_driven | CHARACTER(1) |  |  |  |  | Điều khiển bởi XML |
| alter_names | SMALLINT |  |  |  |  | Cho phép đổi tên |
| cluster_handle | BIGINT |  |  |  |  | Handle của cluster |
| cluster_type | CHARACTER VARYING(100) |  |  |  |  | Loại cluster |
| short_url | BIGINT |  |  |  |  | URL rút gọn |

### Bảng viewentity
| Tên trường | Kiểu dữ liệu và độ dài | Nullable | Unique | P/F Key | Mặc định | Mô tả |
|------------|------------------------|----------|---------|---------|-----------|--------|
| id | BIGINT | X |  | P |  | ID của view entity |
| view_name | CHARACTER VARYING(255) | X |  |  |  | Tên view |
| view_instance_name | CHARACTER VARYING(255) | X |  |  |  | Tên instance của view |
| class_name | CHARACTER VARYING(255) |  |  |  |  | Tên class |
| id_property | CHARACTER VARYING(255) |  |  |  |  | Thuộc tính ID |

### Bảng viewmain
| Tên trường | Kiểu dữ liệu và độ dài | Nullable | Unique | P/F Key | Mặc định | Mô tả |
|------------|------------------------|----------|---------|---------|-----------|--------|
| view_name | CHARACTER VARYING(255) | X |  | P |  | Tên view |
| label | CHARACTER VARYING(255) |  |  |  |  | Nhãn |
| description | CHARACTER VARYING(2048) |  |  |  |  | Mô tả |
| version | CHARACTER VARYING(255) |  |  |  |  | Phiên bản |
| build | CHARACTER VARYING(128) |  |  |  |  | Build |
| resource_type_id | INTEGER |  |  | F |  | ID của resource type |
| icon | CHARACTER VARYING(255) |  |  |  |  | Icon |
| icon64 | CHARACTER VARYING(255) |  |  |  |  | Icon 64px |
| archive | CHARACTER VARYING(255) |  |  |  |  | Archive |
| mask | CHARACTER VARYING(255) |  |  |  |  | Mask |
| system_view | SMALLINT |  |  |  |  | View hệ thống |

### Bảng viewurl
| Tên trường | Kiểu dữ liệu và độ dài | Nullable | Unique | P/F Key | Mặc định | Mô tả |
|------------|------------------------|----------|---------|---------|-----------|--------|
| url_id | BIGINT | X |  | P |  | ID của URL |
| url_name | CHARACTER VARYING(255) | X |  |  |  | Tên URL |
| url_suffix | CHARACTER VARYING(255) | X |  |  |  | Hậu tố URL |

### Bảng viewinstancedata
| Tên trường | Kiểu dữ liệu và độ dài | Nullable | Unique | P/F Key | Mặc định | Mô tả |
|------------|------------------------|----------|---------|---------|-----------|--------|
| view_instance_id | BIGINT | X |  | P |  | ID của view instance |
| view_name | CHARACTER VARYING(255) | X |  |  |  | Tên view |
| view_instance_name | CHARACTER VARYING(255) | X |  |  |  | Tên instance của view |
| name | CHARACTER VARYING(255) | X |  |  |  | Tên |
| user_name | CHARACTER VARYING(255) |  |  |  |  | Tên người dùng |
| value | CHARACTER VARYING(2000) |  |  |  |  | Giá trị |

### Bảng viewinstanceproperty
| Tên trường | Kiểu dữ liệu và độ dài | Nullable | Unique | P/F Key | Mặc định | Mô tả |
|------------|------------------------|----------|---------|---------|-----------|--------|
| view_name | CHARACTER VARYING(255) | X |  | P |  | Tên view |
| view_instance_name | CHARACTER VARYING(255) | X |  | P |  | Tên instance của view |
| name | CHARACTER VARYING(255) | X |  | P |  | Tên thuộc tính |
| value | CHARACTER VARYING(2000) |  |  |  |  | Giá trị |

### Bảng viewparameter
| Tên trường | Kiểu dữ liệu và độ dài | Nullable | Unique | P/F Key | Mặc định | Mô tả |
|------------|------------------------|----------|---------|---------|-----------|--------|
| view_name | CHARACTER VARYING(255) | X |  | P |  | Tên view |
| name | CHARACTER VARYING(255) | X |  | P |  | Tên tham số |
| description | CHARACTER VARYING(2048) |  |  |  |  | Mô tả |
| label | CHARACTER VARYING(255) |  |  |  |  | Nhãn |
| placeholder | CHARACTER VARYING(255) |  |  |  |  | Placeholder |
| default_value | CHARACTER VARYING(2000) |  |  |  |  | Giá trị mặc định |
| cluster_config | CHARACTER VARYING(255) |  |  |  |  | Cấu hình cluster |
| required | CHARACTER(1) |  |  |  |  | Bắt buộc |
| masked | CHARACTER(1) |  |  |  |  | Ẩn giá trị |

### Bảng viewresource
| Tên trường | Kiểu dữ liệu và độ dài | Nullable | Unique | P/F Key | Mặc định | Mô tả |
|------------|------------------------|----------|---------|---------|-----------|--------|
| view_name | CHARACTER VARYING(255) | X |  | P |  | Tên view |
| name | CHARACTER VARYING(255) | X |  | P |  | Tên resource |
| plural_name | CHARACTER VARYING(255) |  |  |  |  | Tên số nhiều |
| id_property | CHARACTER VARYING(255) |  |  |  |  | Thuộc tính ID |
| subresource_names | CHARACTER VARYING(255) |  |  |  |  | Tên subresource |
| provider | CHARACTER VARYING(255) |  |  |  |  | Provider |
| service | CHARACTER VARYING(255) |  |  |  |  | Service |
| resource | CHARACTER VARYING(255) |  |  |  |  | Resource |

### Bảng widget
| Tên trường | Kiểu dữ liệu và độ dài | Nullable | Unique | P/F Key | Mặc định | Mô tả |
|------------|------------------------|----------|---------|---------|-----------|--------|
| id | BIGINT | X |  | P |  | ID của widget |
| widget_name | CHARACTER VARYING(255) | X |  |  |  | Tên widget |
| widget_type | CHARACTER VARYING(255) | X |  |  |  | Loại widget |
| metrics | TEXT |  |  |  |  | Metrics |
| time_created | BIGINT |  |  |  |  | Thời gian tạo |
| author | CHARACTER VARYING(255) |  |  |  |  | Tác giả |
| description | CHARACTER VARYING(2048) |  |  |  |  | Mô tả |
| default_section_name | CHARACTER VARYING(255) |  |  |  |  | Tên section mặc định |
| scope | CHARACTER VARYING(255) |  |  |  |  | Phạm vi |
| widget_values | TEXT |  |  |  |  | Giá trị widget |
| properties | TEXT |  |  |  |  | Thuộc tính |
| cluster_id | BIGINT |  |  | F |  | ID của cluster |

### Bảng widget_layout
| Tên trường | Kiểu dữ liệu và độ dài | Nullable | Unique | P/F Key | Mặc định | Mô tả |
|------------|------------------------|----------|---------|---------|-----------|--------|
| id | BIGINT | X |  | P |  | ID của layout |
| layout_name | CHARACTER VARYING(255) | X |  |  |  | Tên layout |
| section_name | CHARACTER VARYING(255) | X |  |  |  | Tên section |
| scope | CHARACTER VARYING(255) | X |  |  |  | Phạm vi |
| user_name | CHARACTER VARYING(255) |  |  |  |  | Tên người dùng |
| display_name | CHARACTER VARYING(255) |  |  |  |  | Tên hiển thị |
| cluster_id | BIGINT |  |  | F |  | ID của cluster |

### Bảng widget_layout_user_widget
| Tên trường | Kiểu dữ liệu và độ dài | Nullable | Unique | P/F Key | Mặc định | Mô tả |
|------------|------------------------|----------|---------|---------|-----------|--------|
| widget_layout_id | BIGINT | X |  | P |  | ID của widget layout |
| widget_id | BIGINT | X |  | P |  | ID của widget |
| widget_order | SMALLINT |  |  |  |  | Thứ tự widget |

### Bảng topology_logical_task
| Tên trường | Kiểu dữ liệu và độ dài | Nullable | Unique | P/F Key | Mặc định | Mô tả |
|------------|------------------------|----------|---------|---------|-----------|--------|
| id | BIGINT | X |  | P |  | ID của logical task |
| host_task_id | BIGINT |  |  | F |  | ID của host task |
| physical_task_id | BIGINT |  |  | F |  | ID của physical task |
| component | CHARACTER VARYING(255) |  |  |  |  | Component |