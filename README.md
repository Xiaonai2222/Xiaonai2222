import React, { useState } from 'react';
import { Search, Menu, Bell, Home, Compass, BookOpen, User, ChevronRight, Star, Heart, Eye, ArrowLeft, Share2, Download, MessageCircle, ThumbsUp, Gift, Clock, Bookmark, MoreHorizontal } from 'lucide-react';

function App() {
  const [activeTab, setActiveTab] = useState('featured');
  const [currentView, setCurrentView] = useState('home');
  const [selectedManga, setSelectedManga] = useState<number | null>(null);
  const genres = ['Romance', 'Action', 'Comedy', 'Drama', 'Fantasy', 'Horror', 'School', 'Slice of Life'];
  
  const MangaDetailView = ({ id, onBack }: { id: number, onBack: () => void }) => (
    <div className="min-h-screen bg-gray-50">
      {/* Manga Detail Header */}
      <div className="relative h-64">
        <img
          src={`https://source.unsplash.com/800x600?manga&sig=${id}`}
          alt="Manga cover"
          className="w-full h-full object-cover"
        />
        <div className="absolute top-0 left-0 right-0 p-4 flex items-center">
          <button onClick={onBack} className="p-2 rounded-full bg-black/30">
            <ArrowLeft className="w-6 h-6 text-white" />
          </button>
          <div className="flex-1" />
          <button className="p-2 rounded-full bg-black/30 mr-2">
            <Share2 className="w-6 h-6 text-white" />
          </button>
          <button className="p-2 rounded-full bg-black/30">
            <MoreHorizontal className="w-6 h-6 text-white" />
          </button>
        </div>
        <div className="absolute bottom-0 left-0 right-0 p-4 bg-gradient-to-t from-black/80 via-black/50 to-transparent">
          <h1 className="text-2xl font-bold text-white mb-2">Manga Title {id}</h1>
          <div className="flex items-center space-x-4 text-white/90">
            <span className="flex items-center">
              <Eye className="w-4 h-4 mr-1" />
              5.2M
            </span>
            <span className="flex items-center">
              <Star className="w-4 h-4 mr-1 text-yellow-400" />
              4.8
            </span>
            <span className="flex items-center">
              <Heart className="w-4 h-4 mr-1" />
              98K
            </span>
          </div>
        </div>
      </div>

      {/* Action Buttons */}
      <div className="bg-white p-4 flex justify-around border-b">
        <button className="flex flex-col items-center">
          <div className="w-12 h-12 rounded-full bg-red-500 flex items-center justify-center mb-1">
            <BookOpen className="w-6 h-6 text-white" />
          </div>
          <span className="text-xs">Read</span>
        </button>
        <button className="flex flex-col items-center">
          <div className="w-12 h-12 rounded-full bg-gray-100 flex items-center justify-center mb-1">
            <Download className="w-6 h-6 text-gray-600" />
          </div>
          <span className="text-xs">Download</span>
        </button>
        <button className="flex flex-col items-center">
          <div className="w-12 h-12 rounded-full bg-gray-100 flex items-center justify-center mb-1">
            <Gift className="w-6 h-6 text-gray-600" />
          </div>
          <span className="text-xs">Gift</span>
        </button>
        <button className="flex flex-col items-center">
          <div className="w-12 h-12 rounded-full bg-gray-100 flex items-center justify-center mb-1">
            <Bookmark className="w-6 h-6 text-gray-600" />
          </div>
          <span className="text-xs">Bookmark</span>
        </button>
      </div>

      {/* Description */}
      <div className="bg-white p-4 mt-2">
        <h2 className="font-bold mb-2">Description</h2>
        <p className="text-sm text-gray-600 line-clamp-3">
          Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat.
        </p>
        <button className="text-red-500 text-sm mt-2">Read More</button>
      </div>

      {/* Chapters */}
      <div className="bg-white mt-2 p-4">
        <div className="flex justify-between items-center mb-4">
          <h2 className="font-bold">Chapters</h2>
          <button className="text-sm text-gray-500 flex items-center">
            <Clock className="w-4 h-4 mr-1" />
            Latest Update: 2h ago
          </button>
        </div>
        <div className="space-y-4">
          {[1, 2, 3].map((chapter) => (
            <div key={chapter} className="flex items-center justify-between">
              <div className="flex items-center space-x-3">
                <img
                  src={`https://source.unsplash.com/100x100?manga&sig=${id + chapter}`}
                  alt={`Chapter ${chapter}`}
                  className="w-16 h-16 object-cover rounded-lg"
                />
                <div>
                  <h3 className="font-medium">Chapter {chapter}</h3>
                  <p className="text-xs text-gray-500">Updated 2 days ago</p>
                </div>
              </div>
              <button className="px-4 py-1 bg-red-500 text-white rounded-full text-sm">
                Read
              </button>
            </div>
          ))}
        </div>
      </div>

      {/* Comments */}
      <div className="bg-white mt-2 p-4">
        <div className="flex justify-between items-center mb-4">
          <h2 className="font-bold">Comments</h2>
          <span className="text-sm text-gray-500">2.1K</span>
        </div>
        <div className="space-y-4">
          {[1, 2].map((comment) => (
            <div key={comment} className="flex space-x-3">
              <img
                src={`https://source.unsplash.com/50x50?portrait&sig=${comment}`}
                alt="User avatar"
                className="w-8 h-8 rounded-full"
              />
              <div className="flex-1">
                <div className="flex items-center space-x-2">
                  <span className="font-medium text-sm">User {comment}</span>
                  <span className="text-xs text-gray-500">2d ago</span>
                </div>
                <p className="text-sm mt-1">Great chapter! Can't wait for the next one!</p>
                <div className="flex items-center space-x-4 mt-2">
                  <button className="flex items-center text-gray-500 text-xs">
                    <ThumbsUp className="w-3 h-3 mr-1" />
                    24
                  </button>
                  <button className="flex items-center text-gray-500 text-xs">
                    <MessageCircle className="w-3 h-3 mr-1" />
                    Reply
                  </button>
                </div>
              </div>
            </div>
          ))}
        </div>
        <button className="w-full text-center text-red-500 mt-4">View All Comments</button>
      </div>
    </div>
  );

  const HomeView = () => (
    <div className="min-h-screen bg-gray-50">
      {/* Header */}
      <header className="bg-white shadow-sm fixed top-0 left-0 right-0 z-50">
        <div className="flex items-center justify-between px-4 py-3">
          <Menu className="w-6 h-6 text-gray-700" />
          <div className="flex-1 mx-4">
            <div className="relative">
              <input
                type="text"
                placeholder="Search manga"
                className="w-full bg-gray-100 rounded-full py-2 px-4 pl-10 text-sm"
              />
              <Search className="w-4 h-4 absolute left-3 top-2.5 text-gray-400" />
            </div>
          </div>
          <Bell className="w-6 h-6 text-gray-700" />
        </div>

        {/* Category Tabs */}
        <div className="flex space-x-4 px-4 py-2 overflow-x-auto scrollbar-hide">
          <button
            onClick={() => setActiveTab('featured')}
            className={`whitespace-nowrap px-3 py-1 rounded-full text-sm font-medium ${
              activeTab === 'featured' ? 'bg-red-500 text-white' : 'bg-gray-100 text-gray-600'
            }`}
          >
            Featured
          </button>
          <button
            onClick={() => setActiveTab('new')}
            className={`whitespace-nowrap px-3 py-1 rounded-full text-sm font-medium ${
              activeTab === 'new' ? 'bg-red-500 text-white' : 'bg-gray-100 text-gray-600'
            }`}
          >
            New
          </button>
          <button
            onClick={() => setActiveTab('hot')}
            className={`whitespace-nowrap px-3 py-1 rounded-full text-sm font-medium ${
              activeTab === 'hot' ? 'bg-red-500 text-white' : 'bg-gray-100 text-gray-600'
            }`}
          >
            Hot
          </button>
        </div>
      </header>

      {/* Main Content */}
      <main className="pt-28 pb-20">
        {/* Featured Banner */}
        <div className="px-4 mb-6">
          <div className="relative h-48 rounded-xl overflow-hidden">
            <img
              src="https://source.unsplash.com/800x400?manga"
              alt="Featured banner"
              className="w-full h-full object-cover"
            />
            <div className="absolute bottom-0 left-0 right-0 p-4 bg-gradient-to-t from-black/70 to-transparent">
              <h3 className="text-white font-bold">Featured Story</h3>
              <p className="text-white/80 text-sm">Start Reading Now</p>
            </div>
          </div>
        </div>

        {/* Genre Tags */}
        <div className="px-4 mb-6">
          <div className="flex space-x-2 overflow-x-auto pb-2">
            {genres.map((genre) => (
              <button
                key={genre}
                className="px-4 py-1.5 bg-white rounded-full text-sm font-medium border border-gray-200 shadow-sm whitespace-nowrap"
              >
                {genre}
              </button>
            ))}
          </div>
        </div>

        {/* Popular Section */}
        <div className="px-4 mb-6">
          <div className="flex justify-between items-center mb-4">
            <h2 className="text-xl font-bold">Popular Today</h2>
            <div className="flex items-center text-gray-500 text-sm">
              <span>More</span>
              <ChevronRight className="w-4 h-4 ml-1" />
            </div>
          </div>
          <div className="grid grid-cols-2 gap-4">
            {[1, 2, 3, 4].map((item) => (
              <div
                key={item}
                className="bg-white rounded-lg overflow-hidden shadow-sm"
                onClick={() => {
                  setSelectedManga(item);
                  setCurrentView('detail');
                }}
              >
                <div className="relative">
                  <img
                    src={`https://source.unsplash.com/300x400?manga&sig=${item}`}
                    alt={`Manga ${item}`}
                    className="w-full h-48 object-cover"
                  />
                  <div className="absolute top-2 right-2 bg-black/50 rounded-full px-2 py-1 flex items-center">
                    <Star className="w-3 h-3 text-yellow-400 mr-1" />
                    <span className="text-white text-xs">4.8</span>
                  </div>
                </div>
                <div className="p-2">
                  <h3 className="font-semibold text-sm line-clamp-1">Manga Title {item}</h3>
                  <div className="flex items-center space-x-3 mt-1 text-xs text-gray-500">
                    <span className="flex items-center">
                      <Eye className="w-3 h-3 mr-1" />
                      5.2M
                    </span>
                    <span className="flex items-center">
                      <Heart className="w-3 h-3 mr-1" />
                      98K
                    </span>
                  </div>
                  <div className="flex flex-wrap gap-1 mt-2">
                    <span className="text-xs px-2 py-0.5 bg-gray-100 rounded-full">Romance</span>
                    <span className="text-xs px-2 py-0.5 bg-gray-100 rounded-full">Drama</span>
                  </div>
                </div>
              </div>
            ))}
          </div>
        </div>

        {/* New Updates */}
        <div className="px-4">
          <div className="flex justify-between items-center mb-4">
            <h2 className="text-xl font-bold">New Updates</h2>
            <div className="flex items-center text-gray-500 text-sm">
              <span>More</span>
              <ChevronRight className="w-4 h-4 ml-1" />
            </div>
          </div>
          <div className="space-y-4">
            {[1, 2, 3].map((item) => (
              <div
                key={item}
                className="flex space-x-3 bg-white p-3 rounded-lg shadow-sm"
                onClick={() => {
                  setSelectedManga(item);
                  setCurrentView('detail');
                }}
              >
                <img
                  src={`https://source.unsplash.com/150x200?manga&sig=${item + 10}`}
                  alt={`Manga ${item}`}
                  className="w-20 h-28 object-cover rounded-lg"
                />
                <div className="flex-1">
                  <h3 className="font-semibold text-sm mb-1">Latest Update Manga {item}</h3>
                  <div className="flex items-center space-x-2 text-xs text-gray-500 mb-2">
                    <span className="flex items-center">
                      <Eye className="w-3 h-3 mr-1" />
                      3.1M
                    </span>
                    <span className="flex items-center">
                      <Star className="w-3 h-3 mr-1 text-yellow-400" />
                      4.9
                    </span>
                  </div>
                  <div className="flex flex-wrap gap-1">
                    <span className="text-xs px-2 py-0.5 bg-gray-100 rounded-full">Fantasy</span>
                    <span className="text-xs px-2 py-0.5 bg-gray-100 rounded-full">Action</span>
                  </div>
                  <p className="text-xs text-gray-500 mt-2">Updated 2 hours ago</p>
                </div>
              </div>
            ))}
          </div>
        </div>
      </main>

      {/* Bottom Navigation */}
      <nav className="fixed bottom-0 left-0 right-0 bg-white border-t border-gray-200">
        <div className="flex justify-around py-2">
          <button className="flex flex-col items-center px-3 py-1">
            <Home className="w-6 h-6 text-red-500" />
            <span className="text-xs mt-1 text-red-500">Home</span>
          </button>
          <button className="flex flex-col items-center px-3 py-1">
            <Compass className="w-6 h-6 text-gray-400" />
            <span className="text-xs mt-1 text-gray-500">Discover</span>
          </button>
          <button className="flex flex-col items-center px-3 py-1">
            <BookOpen className="w-6 h-6 text-gray-400" />
            <span className="text-xs mt-1 text-gray-500">Library</span>
          </button>
          <button className="flex flex-col items-center px-3 py-1">
            <User className="w-6 h-6 text-gray-400" />
            <span className="text-xs mt-1 text-gray-500">Me</span>
          </button>
        </div>
      </nav>
    </div>
  );

  return (
    <>
      {currentView === 'home' && <HomeView />}
      {currentView === 'detail' && selectedManga && (
        <MangaDetailView
          id={selectedManga}
          onBack={() => {
            setCurrentView('home');
            setSelectedManga(null);
          }}
        />
      )}
    </>
  );
}

export default App;
