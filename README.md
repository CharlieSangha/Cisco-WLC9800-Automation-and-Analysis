# Cisco C9800 WLC Network Device Information Gathering Automation

## Overview
This project automates the collection of comprehensive information from Cisco C9800 Wireless Controllers using Ansible and a Python analysis script. The automation was developed for a work project involving the discovery of 50 C9800 WLCs prior to designing a new solution to consolidate the controllers and implement Cisco Catalyst Center for Automation.

## Prerequisites
- Ansible 2.9+
- Cisco IOS Collection
- Python 3.7+
- Required Python packages:
  - pandas
  - openpyxl
  - logging

## Ansible Features
Automated information gathering from Cisco network devices, collecting comprehensive network infrastructure details:
- Hostname
- System Version
- Interface Configuration
- WLAN Configuration
- NTP Settings
- Access Point Summary
- AAA Server Information
- Full Running Configuration

## Python Script Features
- Robust parsing of multiple text-based configuration files
- Comprehensive data extraction and normalization
- Detailed Excel reporting with multiple sheets:
  - Overview of device configurations
  - WLAN configuration comparison
  - VLAN information
  - NTP server details
  - AAA server configurations
  - Site tag information
- Flexible directory-based input processing
- Comprehensive error handling and logging
- Command-line argument support for customization

## Installation
1. Install Ansible and required collections:
```bash
pip install ansible
```
Reference: https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html

2. Configure your inventory file with device details:
```ini
[cisco_devices]
# Replace with your actual device details
wireless_controller1 ansible_host=10.0.0.2
wireless_controller2 ansible_host=10.0.0.3
wireless_controller3 ansible_host=10.0.0.4
```

## Usage

### Ansible Collection
```bash
ansible-playbook -i {inventory file} {playbook yaml}
```

### Python Analysis Script
```bash
python wlc_comparison_tool.py --base-dir ./device_info --output wlc_comparison_report.xlsx
```

### Command-line Arguments
- `--base-dir`: Directory containing device subdirectories (default: `./device_info`)
- `--output`: Output Excel filename (default: `wlc_comparison_report.xlsx`)

## Repository Structure
```
.
├── README.md
├── sample_inventory
├── device_info_playbook.yml
├── wlc_comparison_tool.py
└── screenshots/
    ├── screenshot-description.md
    ├── Parent-Folder-Screenshot.png
    ├── Sub-Folder-Screenshot.png
    ├── Sample-Excel-WLAN-Tab-screenshot.png
    ├── Sample-Excel-Summary-screenshot.png
    └── Sample-ap-output-screenshot.png
```

## Example Output
Information is saved in `./device_info/[hostname]/` directory with files:
- `hostname.txt`
- `version.txt`
- `interfaces.txt`
- `wlan.txt`
- `ntp.txt`
- `ap_summary.txt`
- `tag_site.txt`
- `aaa_servers.txt`
- `running-config.txt`

### Excel Report Sheets
1. **Overview**: Quick summary of devices
2. **WLANs**: Detailed WLAN configuration comparison
3. **VLANs**: VLAN details across devices
4. **NTP Servers**: NTP server configurations
5. **AAA Servers**: Authentication server details
6. **Site Tags**: Wireless site tag information

## Security Considerations
- Use `ansible-vault` to encrypt sensitive information
- Implement least-privilege access
- Avoid hardcoding credentials

## Logging
The script provides detailed logging to help diagnose any issues during processing.

## Future Improvements
- Implement more robust error handling
- Create more advanced comparative analysis between devices
- Fix minor formatting issues to Excel output
- Include the AP Summary as an output in Excel. 
- Add support for additional network device types

## Contributing
Pull requests are welcome. For major changes, please open an issue first to discuss what you would like to change.

## Disclaimer
This tool is provided as-is and is intended to assist in network configuration management. Always verify configurations manually.

## License
[Specify your license here]
