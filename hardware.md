# **Hardware**

For a functional LLM environment, the graphics card (GPU) is the most important component. The more video memory available, the larger the models that can be loaded; larger models generally perform better than smaller ones.

### **Our Configuration**

We chose this configuration because at the time of purchase (December 2024), it offered a good price-to-performance ratio. Of course, you can deviate from these specifications.  

Tip: Check Tweakers for the most up-to-date computer hardware prices. https://tweakers.net/pricewatch/

- **GPU**: [INNO3D GeForce RTX 4070 SUPER TWIN X2](https://www.inno3d.com/products_detail.php?refid=909) (12GB VRAM)  
  - Depending on price developments, another GPU might be more cost-effective  
  - For heavier use cases, consider a GPU with more memory  
- **CPU**: Intel Core i5-12600K or equivalent  
- **Motherboard**: ASUS PRIME B760-PLUS D4  
- **RAM**: 64 GB DDR4 (e.g., Corsair Vengeance LPX CMK64GX4M2E3200C16)  
- **Storage**: 2TB NVMe SSD (e.g., WD Black SN770)  
- **Power Supply**: 750W or higher (80+ Gold certification recommended)  
- **Cooling**: CPU cooler such as Noctua NH-L12S  
- **Case**: Choose a mid-tower or full-tower with good airflow  

**Note**: The models themselves are very large—several GBs. A smaller storage drive can fill up quickly. Also, when you upload files for the LLM to use, they are stored locally as well.

### **Hardware Guide: Which GPU for Which Models?**

| GPU Model    | VRAM | Max Model Size    | Recommended Models                   | Estimated Cost |
|--------------|------|-------------------|---------------------------------------|----------------|
| RTX 4060     | 8GB  | Up to 7B params   | Gemma-7b, Phi-2, Qwen-7b              | €300-€350      | 
| RTX 4070 Super | 12GB | Up to 14B params | DeepSeek-R1-14b, Phi-3-mini, Qwen-14b | €550-€650      | 
| RTX 4080     | 16GB | Up to 20B params  | Mistral-Large, Llama3-8x2             | €800-€1000     |
| RTX 4090     | 24GB | Up to 30–40B params | Llama-3-70b (quantized), Mixtral-8x7b | €1400-€1800    | 
| 2x RTX 4090  | 48GB | 70B+ params       | DeepSeek-V2, Llama-3-70b              | €2800-€3600    |

**Explanation**: Smaller models (7B) work perfectly fine in an experimental environment.

### **Key Considerations for Hardware Selection**

- **GPU memory**: Determines which models you can run and how many simultaneously.  
- **Case**: Choose a spacious case with good airflow for adequate cooling.  
- **Internet connection**: A stable internet connection is required to download models and possibly to provide access to users.  
- **Power consumption**: More powerful GPUs consume more electricity.  

The total cost for the recommended configuration is around €1,100, which is a one-time investment compared to recurring subscription costs for commercial AI services.
