import React, { useState, useRef } from 'react';
import { Upload, Download, ImageIcon, RefreshCw, Check, X, FileImage, Zap } from 'lucide-react';

const ImageConverter = () => {
  const [selectedFile, setSelectedFile] = useState(null);
  const [previewUrl, setPreviewUrl] = useState(null);
  const [outputFormat, setOutputFormat] = useState('jpeg');
  const [quality, setQuality] = useState(0.9);
  const [isConverting, setIsConverting] = useState(false);
  const [convertedUrl, setConvertedUrl] = useState(null);
  const [originalFormat, setOriginalFormat] = useState('');
  const [fileSize, setFileSize] = useState({ original: 0, converted: 0 });
  const fileInputRef = useRef(null);
  const canvasRef = useRef(null);

  const supportedFormats = [
    { value: 'jpeg', label: 'JPEG', extension: '.jpg', description: 'High compression, smaller files' },
    { value: 'png', label: 'PNG', extension: '.png', description: 'Lossless, supports transparency' },
    { value: 'webp', label: 'WebP', extension: '.webp', description: 'Modern format, excellent compression' },
    { value: 'bmp', label: 'BMP', extension: '.bmp', description: 'Uncompressed, large files' },
    { value: 'gif', label: 'GIF', extension: '.gif', description: 'Supports animation, limited colors' }
  ];

  const formatFileSize = (bytes) => {
    if (bytes === 0) return '0 Bytes';
    const k = 1024;
    const sizes = ['Bytes', 'KB', 'MB', 'GB'];
    const i = Math.floor(Math.log(bytes) / Math.log(k));
    return parseFloat((bytes / Math.pow(k, i)).toFixed(2)) + ' ' + sizes[i];
  };

  const dataURLtoBlob = (dataURL) => {
    const arr = dataURL.split(',');
    const mime = arr[0].match(/:(.*?);/)[1];
    const bstr = atob(arr[1]);
    let n = bstr.length;
    const u8arr = new Uint8Array(n);
    while (n--) {
      u8arr[n] = bstr.charCodeAt(n);
    }
    return new Blob([u8arr], { type: mime });
  };

  const handleFileSelect = (event) => {
    const file = event.target.files[0];
    if (file && file.type.startsWith('image/')) {
      setSelectedFile(file);
      setOriginalFormat(file.type.split('/')[1].toUpperCase());
      setFileSize(prev => ({ ...prev, original: file.size }));
      
      const reader = new FileReader();
      reader.onload = (e) => {
        setPreviewUrl(e.target.result);
      };
      reader.readAsDataURL(file);
      
      // Reset converted image
      setConvertedUrl(null);
      setFileSize(prev => ({ ...prev, converted: 0 }));
    }
  };

  const handleDragOver = (e) => {
    e.preventDefault();
    e.currentTarget.classList.add('border-indigo-400', 'bg-indigo-50');
  };

  const handleDragLeave = (e) => {
    e.preventDefault();
    e.currentTarget.classList.remove('border-indigo-400', 'bg-indigo-50');
  };

  const handleDrop = (e) => {
    e.preventDefault();
    e.currentTarget.classList.remove('border-indigo-400', 'bg-indigo-50');
    const file = e.dataTransfer.files[0];
    if (file && file.type.startsWith('image/')) {
      const event = { target: { files: [file] } };
      handleFileSelect(event);
    }
  };

  const convertImage = () => {
    if (!selectedFile || !previewUrl) return;

    setIsConverting(true);
    
    const canvas = canvasRef.current;
    const ctx = canvas.getContext('2d');
    const img = new Image();
    
    img.onload = () => {
      canvas.width = img.width;
      canvas.height = img.height;
      
      // Clear canvas
      ctx.clearRect(0, 0, canvas.width, canvas.height);
      
      // For formats that don't support transparency, fill with white background
      if (outputFormat === 'jpeg' || outputFormat === 'bmp') {
        ctx.fillStyle = '#FFFFFF';
        ctx.fillRect(0, 0, canvas.width, canvas.height);
      }
      
      ctx.drawImage(img, 0, 0);
      
      // Convert to desired format
      let mimeType = `image/${outputFormat}`;
      let qualityValue = (outputFormat === 'png' || outputFormat === 'gif') ? undefined : quality;
      
      const convertedDataUrl = canvas.toDataURL(mimeType, qualityValue);
      setConvertedUrl(convertedDataUrl);
      
      // Calculate converted file size
      const convertedBlob = dataURLtoBlob(convertedDataUrl);
      setFileSize(prev => ({ ...prev, converted: convertedBlob.size }));
      
      setIsConverting(false);
    };
    
    img.onerror = () => {
      setIsConverting(false);
      alert('Error loading image. Please try a different file.');
    };
    
    img.src = previewUrl;
  };

  const downloadImage = () => {
    if (!convertedUrl) return;
    
    try {
      const link = document.createElement('a');
      const format = supportedFormats.find(f => f.value === outputFormat);
      const timestamp = new Date().toISOString().slice(0, 19).replace(/:/g, '-');
      const fileName = `converted-${timestamp}${format.extension}`;
      
      // Convert data URL to blob for better download handling
      const blob = dataURLtoBlob(convertedUrl);
      const url = URL.createObjectURL(blob);
      
      link.href = url;
      link.download = fileName;
      link.style.display = 'none';
      
      document.body.appendChild(link);
      link.click();
      document.body.removeChild(link);
      
      // Clean up the URL object
      setTimeout(() => URL.revokeObjectURL(url), 100);
      
    } catch (error) {
      console.error('Download failed:', error);
      alert('Download failed. Please try again.');
    }
  };

  const resetConverter = () => {
    setSelectedFile(null);
    setPreviewUrl(null);
    setConvertedUrl(null);
    setOriginalFormat('');
    setFileSize({ original: 0, converted: 0 });
    if (fileInputRef.current) {
      fileInputRef.current.value = '';
    }
  };

  return (
    <div className="min-h-screen bg-gradient-to-br from-slate-50 via-blue-50 to-indigo-100 p-4 sm:p-6 lg:p-8">
      <div className="max-w-6xl mx-auto">
        {/* Header */}
        <div className="text-center mb-8 lg:mb-12">
          <div className="flex items-center justify-center mb-4">
            <div className="bg-gradient-to-r from-indigo-500 to-purple-600 p-3 rounded-xl shadow-lg mr-3">
              <ImageIcon className="w-8 h-8 text-white" />
            </div>
            <h1 className="text-3xl lg:text-4xl font-bold bg-gradient-to-r from-gray-800 to-gray-600 bg-clip-text text-transparent">
              Image Format Converter
            </h1>
          </div>
          <p className="text-gray-600 text-lg max-w-2xl mx-auto">
            Convert your images between different formats with professional quality and ease
          </p>
        </div>

        {/* Main Content Grid */}
        <div className="grid lg:grid-cols-3 gap-6 lg:gap-8">
          
          {/* Upload Section */}
          <div className="lg:col-span-1">
            <div className="bg-white/80 backdrop-blur-sm rounded-2xl shadow-xl border border-white/20 p-6 h-full">
              <h2 className="text-xl font-semibold text-gray-800 mb-4 flex items-center">
                <Upload className="w-5 h-5 mr-2 text-indigo-600" />
                Upload Image
              </h2>
              
              {!selectedFile ? (
                <div
                  className="border-2 border-dashed border-gray-300 rounded-xl p-8 text-center hover:border-indigo-400 transition-all duration-300 cursor-pointer group"
                  onDragOver={handleDragOver}
                  onDragLeave={handleDragLeave}
                  onDrop={handleDrop}
                  onClick={() => fileInputRef.current?.click()}
                >
                  <div className="group-hover:scale-110 transition-transform duration-300">
                    <FileImage className="w-16 h-16 text-gray-400 mx-auto mb-4 group-hover:text-indigo-500" />
                  </div>
                  <p className="text-gray-600 mb-2 font-medium">Drag & drop your image here</p>
                  <p className="text-sm text-gray-500 mb-4">Supports PNG, JPEG, WebP, BMP, GIF</p>
                  <button className="bg-gradient-to-r from-indigo-600 to-purple-600 text-white px-6 py-3 rounded-lg hover:from-indigo-700 hover:to-purple-700 transition-all duration-300 font-medium shadow-lg">
                    Choose File
                  </button>
                </div>
              ) : (
                <div className="space-y-4">
                  <div className="relative group">
                    <img
                      src={previewUrl}
                      alt="Preview"
                      className="w-full h-64 object-contain bg-gradient-to-br from-gray-50 to-gray-100 rounded-xl border-2 border-gray-200"
                    />
                    <div className="absolute top-3 right-3 bg-gradient-to-r from-green-500 to-emerald-500 text-white px-3 py-1 rounded-full text-sm font-semibold shadow-lg">
                      {originalFormat}
                    </div>
                    <button
                      onClick={resetConverter}
                      className="absolute top-3 left-3 bg-red-500 hover:bg-red-600 text-white p-2 rounded-full transition-colors shadow-lg opacity-0 group-hover:opacity-100"
                    >
                      <X className="w-4 h-4" />
                    </button>
                  </div>
                  
                  <div className="bg-gray-50 rounded-lg p-4">
                    <p className="text-sm text-gray-600 truncate font-medium mb-1">
                      📁 {selectedFile.name}
                    </p>
                    <p className="text-sm text-gray-500">
                      📊 Size: {formatFileSize(fileSize.original)}
                    </p>
                  </div>
                </div>
              )}
              
              <input
                ref={fileInputRef}
                type="file"
                accept="image/*"
                onChange={handleFileSelect}
                className="hidden"
              />
            </div>
          </div>

          {/* Conversion Settings */}
          <div className="lg:col-span-1">
            <div className="bg-white/80 backdrop-blur-sm rounded-2xl shadow-xl border border-white/20 p-6 h-full">
              <h2 className="text-xl font-semibold text-gray-800 mb-4 flex items-center">
                <Zap className="w-5 h-5 mr-2 text-indigo-600" />
                Conversion Settings
              </h2>
              
              <div className="space-y-6">
                <div>
                  <label className="block text-sm font-medium text-gray-700 mb-3">
                    Output Format
                  </label>
                  <div className="space-y-2">
                    {supportedFormats.map((format) => (
                      <label
                        key={format.value}
                        className={`flex items-center p-3 rounded-lg border-2 cursor-pointer transition-all duration-200 ${
                          outputFormat === format.value
                            ? 'border-indigo-500 bg-indigo-50'
                            : 'border-gray-200 hover:border-gray-300'
                        }`}
                      >
                        <input
                          type="radio"
                          name="format"
                          value={format.value}
                          checked={outputFormat === format.value}
                          onChange={(e) => setOutputFormat(e.target.value)}
                          className="sr-only"
                        />
                        <div className="flex-1">
                          <div className="flex items-center justify-between">
                            <span className="font-medium text-gray-800">{format.label}</span>
                            <span className="text-sm text-gray-500">{format.extension}</span>
                          </div>
                          <p className="text-xs text-gray-500 mt-1">{format.description}</p>
                        </div>
                      </label>
                    ))}
                  </div>
                </div>

                {outputFormat !== 'png' && outputFormat !== 'gif' && (
                  <div>
                    <label className="block text-sm font-medium text-gray-700 mb-3">
                      Quality: {Math.round(quality * 100)}%
                    </label>
                    <div className="relative">
                      <input
                        type="range"
                        min="0.1"
                        max="1"
                        step="0.1"
                        value={quality}
                        onChange={(e) => setQuality(parseFloat(e.target.value))}
                        className="w-full h-2 bg-gradient-to-r from-red-200 via-yellow-200 to-green-200 rounded-lg appearance-none cursor-pointer"
                        style={{
                          background: `linear-gradient(to right, #fecaca 0%, #fde68a 50%, #bbf7d0 100%)`
                        }}
                      />
                      <div className="flex justify-between text-xs text-gray-500 mt-1">
                        <span>Low</span>
                        <span>High</span>
                      </div>
                    </div>
                  </div>
                )}

                <button
                  onClick={convertImage}
                  disabled={!selectedFile || isConverting}
                  className="w-full bg-gradient-to-r from-indigo-600 to-purple-600 text-white py-4 px-6 rounded-xl hover:from-indigo-700 hover:to-purple-700 disabled:from-gray-400 disabled:to-gray-400 disabled:cursor-not-allowed transition-all duration-300 flex items-center justify-center font-medium shadow-lg text-lg"
                >
                  {isConverting ? (
                    <>
                      <RefreshCw className="w-5 h-5 mr-2 animate-spin" />
                      Converting...
                    </>
                  ) : (
                    <>
                      <RefreshCw className="w-5 h-5 mr-2" />
                      Convert Image
                    </>
                  )}
                </button>
              </div>
            </div>
          </div>

          {/* Result Section */}
          <div className="lg:col-span-1">
            {convertedUrl ? (
              <div className="bg-white/80 backdrop-blur-sm rounded-2xl shadow-xl border border-white/20 p-6 h-full">
                <h2 className="text-xl font-semibold text-gray-800 mb-4 flex items-center">
                  <Check className="w-5 h-5 mr-2 text-green-600" />
                  Converted Result
                </h2>
                
                <div className="space-y-4">
                  <div className="relative">
                    <img
                      src={convertedUrl}
                      alt="Converted"
                      className="w-full h-64 object-contain bg-gradient-to-br from-gray-50 to-gray-100 rounded-xl border-2 border-gray-200"
                    />
                    <div className="absolute top-3 right-3 bg-gradient-to-r from-blue-500 to-indigo-500 text-white px-3 py-1 rounded-full text-sm font-semibold shadow-lg">
                      {outputFormat.toUpperCase()}
                    </div>
                  </div>
                  
                  <div className="bg-gray-50 rounded-lg p-4 space-y-2">
                    <div className="flex justify-between items-center">
                      <span className="text-sm text-gray-600">Original:</span>
                      <span className="text-sm font-medium">{formatFileSize(fileSize.original)}</span>
                    </div>
                    <div className="flex justify-between items-center">
                      <span className="text-sm text-gray-600">Converted:</span>
                      <span className="text-sm font-medium">{formatFileSize(fileSize.converted)}</span>
                    </div>
                    <div className="flex justify-between items-center pt-2 border-t border-gray-200">
                      <span className="text-sm text-gray-600">Compression:</span>
                      <span className={`text-sm font-medium ${
                        fileSize.converted < fileSize.original ? 'text-green-600' : 'text-red-600'
                      }`}>
                        {fileSize.original > 0 ? 
                          `${Math.round(((fileSize.original - fileSize.converted) / fileSize.original) * 100)}%` 
                          : '0%'
                        }
                      </span>
                    </div>
                  </div>
                  
                  <button
                    onClick={downloadImage}
                    className="w-full bg-gradient-to-r from-green-600 to-emerald-600 text-white py-4 px-6 rounded-xl hover:from-green-700 hover:to-emerald-700 transition-all duration-300 inline-flex items-center justify-center font-medium shadow-lg text-lg"
                  >
                    <Download className="w-5 h-5 mr-2" />
                    Download Image
                  </button>
                </div>
              </div>
            ) : (
              <div className="bg-white/30 backdrop-blur-sm rounded-2xl border-2 border-dashed border-gray-300 p-6 h-full flex items-center justify-center">
                <div className="text-center">
                  <ImageIcon className="w-16 h-16 text-gray-400 mx-auto mb-4" />
                  <p className="text-gray-500 font-medium">Converted image will appear here</p>
                  <p className="text-sm text-gray-400 mt-2">Upload and convert an image to see the result</p>
                </div>
              </div>
            )}
          </div>
        </div>
        
        {/* Hidden canvas for conversion */}
        <canvas ref={canvasRef} className="hidden" />
        
        {/* Footer */}
        <div className="text-center mt-12 text-gray-500 text-sm">
          <p>✨ Professional image conversion with maintained quality ✨</p>
        </div>
      </div>
    </div>
  );
};

export default ImageConverter;
