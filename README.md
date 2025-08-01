# hotel_bookings_project
project sector:*Tourism and Hospitality*
 Project: *Hotel Booking Cancellation & Demand Analysis* 


- Noella Twiringiyimana 26749 
-  Introduction to Big Data   
- Group E  
   



>Project Overview<

This project analyzes hotel booking data to uncover patterns in guest behavior and booking cancellations. Using Python for analysis and Power BI for dashboards, the project helps identify insights that can support better hotel management decisions.

---

# Tools Used

| Tool        | Purpose                        |
|-------------|--------------------------------|
| Python      | Data cleaning and analysis     |
| Power BI    | Interactive dashboard creation |
| Git & GitHub| Project organization & version control |

---

# Dataset Information

- File Used:`clean_hotel_bookings.csv`
- Includes:  
  - Booking status (`is_canceled`)  
  - Lead time (days before arrival)  
  - Average daily rate (`adr`)  
  - Stay duration (weekend and weekday nights)  
  - Arrival month and hotel type

---

# Python Analysis

Notebook: `Hotel_analysis.ipynb`
<img width="1366" height="728" alt="Lead time" src="https://github.com/user-attachments/assets/66df43f9-35c3-414e-8ecd-25b16b3c9f70" />
# Key Tasks:
- Data cleaning and inspection
- Created new column: `lead_time_group`
- Analyzed cancellation behavior by how early people booked (lead time)
<img width="1366" height="728" alt="cleaned_dataset" src="https://github.com/user-attachments/assets/233914a9-35e9-47a0-9a91-ee134ff85fde" />
--- <img width="1366" height="728" alt="after cleaning" src="https://github.com/user-attachments/assets/e721a91c-36fe-4ba1-b849-b71dbee62c65" />
 
Power BI visualization dashboard:
#<img width="1366" height="728" alt="screenshoot6" src="https://github.com/user-attachments/assets/47449482-b075-4cd6-8167-4297c3bc38d1" />
<img width="1366" height="728" alt="screenshoot5" src="https://github.com/user-attachments/assets/b4fead70-850b-4230-adb8-583180954e05" />
<img width="1366" height="728" alt="screenshoot4" src="https://github.com/user-attachments/assets/09a3b579-d451-45b7-927f-790b35b4793a" />
<img width="1366" height="728" alt="screenshoot3" src="https://github.com/user-attachments/assets/619df1f8-e456-4895-96aa-9c1c628165af" />
<img width="1366" height="728" alt="screenshoot2" src="https://github.com/user-attachments/assets/d4f663f4-9fd8-44f9-a5c1-1707c84f5676" />
<img width="1366" height="728" alt="screenshoot1" src="https://github.com/user-attachments/assets/7d0855d9-8c13-4d88-be65-03351ef1db00" />

<img width="1366" height="728" alt="Deposit type" src="https://github.com/user-attachments/assets/27aa3d36-0b99-4059-a84e-c9af73a0ef3e" />
<img width="1200" height="728" alt="Dataset" src="https://github.com/user-attachments/assets/da9c9d8a-6fa6-4080-aa59-7b4d6eb531b4" />

<img width="1366" height="728" alt="cancellation month" src="https://github.com/user-attachments/assets/31d430db-5265-4074-97f2-b84ebb950e98" />
<img width="1366" height="728" alt="Booking_cancellation" src="https://github.com/user-attachments/assets/df265de8-8564-4a3c-9a09-b61ba9c9bd22" />
<img width="1200" height="728" alt="innovation" src="https://github.com/user-attachments/assets/e71d5a1e-3ca4-48bd-9169-04d6c9f8c540" />


 New Innovation: Lead Time vs Cancellation

I grouped bookings by **how far in advance** the guest booked:

```python
def lead_time_group(lead):
    if lead <= 7:
        return '0-7 days'
    elif lead <= 30:
        return '8-30 days'
    elif lead <= 90:
        return '31-90 days'
    else:
        return '90+ days'

df['lead_time_group'] = df['lead_time'].apply(lead_time_group)

# Cancellation rate by group
cancellation_rate = df.groupby('lead_time_group')['is_canceled'].mean().reset_index()
cancellation_rate['is_canceled'] = (cancellation_rate['is_canceled'] * 100).round(2)
cancellation_rate.rename(columns={'is_canceled': 'Cancellation Rate (%)'}, inplace=True)

print(cancellation_rate)

