# YVENTY
import React, { useState } from "react";
import { Camera, Plus, Users } from "lucide-react";

function EmptyAthleteProfile() {
  const [profileImage, setProfileImage] = useState(null);

  const handleImageUpload = (event) => {
    const file = event.target.files[0];
    if (file) {
      const reader = new FileReader();
      reader.onload = (e) => setProfileImage(e.target.result);
      reader.readAsDataURL(file);
    }
  };

  return (
    <div className="min-h-screen bg-white p-4">
      <div className="max-w-2xl mx-auto bg-white rounded-lg p-6">
        {/* Horné tlačidlá */}
        <div className="flex justify-between mb-8">
          <button className="text-gray-700 hover:text-gray-900">
            Profil
          </button>
          <button className="text-gray-700 hover:text-gray-900">
            Zdielať
          </button>
        </div>

        {/* Foto sekcia */}
        <div className="flex flex-col items-center mb-12">
          <div className="relative w-32 h-32 group">
            <input
              type="file"
              accept="image/*"
              onChange={handleImageUpload}
              className="hidden"
              id="profilePhotoInput"
            />
            <label
              htmlFor="profilePhotoInput"
              className="cursor-pointer w-full h-full block"
            >
              <div
                className={`
                w-full h-full rounded-full overflow-hidden
                ${!profileImage ? "bg-gray-100" : ""}
                flex items-center justify-center
                group-hover:bg-gray-200 transition-colors
              `}
              >
                {profileImage ? (
                  <img
                    src={profileImage}
                    alt="Profile"
                    className="w-full h-full object-cover"
                  />
                ) : (
                  <Camera
                    size={32}
                    className="text-blue-500 group-hover:text-blue-600"
                    strokeWidth={1.5}
                  />
                )}
              </div>
            </label>
          </div>
          <p className="text-gray-600 mt-4">Popis</p>
        </div>

        {/* Prázdny priestor pre eventy */}
        <div>
          <div className="flex justify-between items-center mb-4">
            <span className="text-sm text-gray-500">
              Duplikovať týžden
            </span>
            <div className="flex items-center text-sm text-gray-500">
              <Users size={16} className="mr-1" />
              <span>30 follows</span>
            </div>
          </div>
          <div className="bg-gray-50 rounded-lg p-8 border border-gray-100 relative h-48 hover:bg-gray-100 transition-colors">
            <div className="absolute inset-0 flex items-center justify-center">
              <Plus size={64} className="text-blue-500" strokeWidth={1.5} />
            </div>
          </div>
        </div>
      </div>
    </div>
  );
}

export default EmptyAthleteProfile;
 

